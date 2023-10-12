# 螺旋矩阵

> 难度：中等
>
> 次数：2
>
> https://leetcode.cn/problems/spiral-matrix

## 题目

给你一个`m`行`n`列的矩阵`matrix`，请按照**顺时针螺旋顺序**，返回矩阵中的所有元素。

### 示例

#### 示例 1：

![spiral1](https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg)

```
输入：matrix = [[1,2,3],[4,5,6],[7,8,9]]
输出：[1,2,3,6,9,8,7,4,5]
```

#### 示例 2：

![spiral](https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg)

```
输入：matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
输出：[1,2,3,4,8,12,11,10,9,5,6,7]
```

## 解法

### 模拟行为

```javascript
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var spiralOrder = function (matrix) {
  const m = matrix.length // 行数
  const n = matrix[0].length // 列数
  const count = m * n // 总次数
  const res = []
  let loop = Math.floor(count / 4) // 循环次数

  if (m === 1) {
    return matrix[0]
  } else if (n === 1) {
    return matrix.map(item => item[0])
  } else {
    let offset = 1
    let startX = 0,
      startY = 0

    while (loop--) {
      let row = startX,
        col = startY

      for (; col < startY + n - offset; col++) {
        res.push(matrix[row][col])
        if (res.length === count) {
          return res
        }
      }

      for (; row < startX + m - offset; row++) {
        res.push(matrix[row][col])
        if (res.length === count) {
          return res
        }
      }

      for (; col > startY; col--) {
        res.push(matrix[row][col])
        if (res.length === count) {
          return res
        }
      }

      for (; row > startX; row--) {
        res.push(matrix[row][col])
        if (res.length === count) {
          return res
        }
      }

      startX++
      startY++
      offset += 2
    }

    if (count % 2 !== 0) {
      const middleX = Math.floor(m / 2)
      const middleY = Math.floor(n / 2)
      res.push(matrix[middleX][middleY])
    }
  }

  return res
}
```
