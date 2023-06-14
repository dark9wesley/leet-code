# N 皇后 II

> 难度：困难
>
> 次数：1
>
> https://leetcode.cn/problems/n-queens-ii

## 题目

**n 皇后问题** 研究的是如何将 `n` 个皇后放置在 `n × n` 的棋盘上，并且使皇后彼此之间不能相互攻击。

给你一个整数 `n` ，返回 **n 皇后问题** 不同的解决方案的数量。

### 示例

#### 示例 1：

![queens](https://assets.leetcode.com/uploads/2020/11/13/queens.jpg)

```
输入：n = 4
输出：2
解释：如上图所示，4 皇后问题存在两个不同的解法。
```

#### 示例 2：

```
输入：n = 1
输出：1
```

## 解法

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var totalNQueens = function (n) {
  let result = 0
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

  const backTracking = row => {
    if (row === n) {
      result++
      return
    }

    for (let col = 0; col < n; col++) {
      if (isValid(row, col)) {
        chessBoard[row][col] = 'Q'
        backTracking(row + 1)
        chessBoard[row][col] = '.'
      }
    }
  }

  backTracking(0)

  return result
}
```
