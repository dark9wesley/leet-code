# 解数独

> 难度：困难
>
> 次数：1
>
> https://leetcode.cn/problems/sudoku-solver

## 题目

编写一个程序，通过填充空格来解决数独问题。

数独的解法需 **遵循如下规则：**

- 数字 `1-9` 在每一行只能出现一次。
- 数字 `1-9` 在每一列只能出现一次。
- 数字 `1-9` 在每一个以粗实线分隔的 `3x3` 宫内只能出现一次。（请参考示例图）

数独部分空格内已填入了数字，空白格用 `'.'` 表示。

### 示例

#### 示例 1：

![20050714svg](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2021/04/12/250px-sudoku-by-l2g-20050714svg.png)

```
输入：board = [
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
输出：[
  ["5","3","4","6","7","8","9","1","2"],
  ["6","7","2","1","9","5","3","4","8"],
  ["1","9","8","3","4","2","5","6","7"],
  ["8","5","9","7","6","1","4","2","3"],
  ["4","2","6","8","5","3","7","9","1"],
  ["7","1","3","9","2","4","8","5","6"],
  ["9","6","1","5","3","7","2","8","4"],
  ["2","8","7","4","1","9","6","3","5"],
  ["3","4","5","2","8","6","1","7","9"]
]
```

## 解法

```javascript
/**
 * @param {character[][]} board
 * @return {void} Do not return anything, modify board in-place instead.
 */
var solveSudoku = function (board) {
  function isValid(row, col, num) {
    const length = board.length
    for (let i = 0; i < length; i++) {
      if (board[row][i] === num) {
        return false
      }
    }

    for (let i = 0; i < length; i++) {
      if (board[i][col] === num) {
        return false
      }
    }

    const startRow = Math.floor(row / 3) * 3
    const startCol = Math.floor(col / 3) * 3

    for (let i = startRow; i < startRow + 3; i++) {
      for (let j = startCol; j < startCol + 3; j++) {
        if (board[i][j] === num) {
          return false
        }
      }
    }

    return true
  }

  const backtracking = () => {
    for (let i = 0; i < board.length; i++) {
      for (let j = 0; j < board[0].length; j++) {
        if (board[i][j] !== '.') {
          continue
        }
        for (let num = 1; num <= 9; num++) {
          if (isValid(i, j, `${num}`)) {
            board[i][j] = `${num}`
            if (backtracking()) {
              return true
            }
            board[i][j] = '.'
          }
        }
        return false
      }
    }
    return true
  }

  backtracking()
}
```
