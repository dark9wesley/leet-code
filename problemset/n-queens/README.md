# N 皇后

> 难度：困难
>
> 次数：1
>
> https://leetcode.cn/problems/n-queens

## 题目

按照国际象棋的规则，皇后可以攻击与之处在同一行或同一列或同一斜线上的棋子。

**n 皇后问题** 研究的是如何将 `n` 个皇后放置在 `n×n` 的棋盘上，并且使皇后彼此之间不能相互攻击。

给你一个整数 `n` ，返回所有不同的 **n 皇后问题** 的解决方案。

每一种解法包含一个不同的 **n 皇后问题** 的棋子放置方案，该方案中 `'Q'` 和 `'.'` 分别代表了皇后和空位。

### 示例

#### 示例 1：

![queens](https://assets.leetcode.com/uploads/2020/11/13/queens.jpg)

```
输入：n = 4
输出：[[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
解释：如上图所示，4 皇后问题存在两个不同的解法。
```

#### 示例 2：

```
输入：n = 1
输出：[["Q"]]
```

## 解法

```javascript
/**
 * @param {number} n
 * @return {string[][]}
 */
var solveNQueens = function (n) {
  const result = []
  const chessBoard = new Array(n).fill([]).map(() => new Array(n).fill('.'))

  function isValid(row, col) {
    for (let i = 0; i < row; i++) {
      if (chessBoard[i][col] === 'Q') {
        return false
      }
    }

    for (let i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--) {
      if (chessBoard[i][j] === 'Q') {
        return false
      }
    }

    for (let i = row - 1, j = col + 1; i >= 0 && j < n; i--, j++) {
      if (chessBoard[i][j] === 'Q') {
        return false
      }
    }

    return true
  }

  function transformChessBoard(chessBoard) {
    let chessBoardBack = []
    for (const row of chessBoard) {
      let rowStr = ''
      for (const s of row) {
        rowStr += s
      }
      chessBoardBack.push(rowStr)
    }
    return chessBoardBack
  }

  const backTracking = row => {
    if (row === n) {
      result.push(transformChessBoard(chessBoard))
      return
    }

    for (let col = 0; col < n; col++) {
      if (isValid(row, col)) {
        chessBoard[row][col] = 'Q'
        console.log(chessBoard)
        backTracking(row + 1)
        chessBoard[row][col] = '.'
      }
    }
  }

  backTracking(0)

  return result
}
```
