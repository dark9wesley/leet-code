# 螺旋矩阵

> 难度：中等
>
> 次数：1
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
const spiralOrder = function (matrix) {
  let startX = 0
  let startY = 0
  const m = matrix.length
  const n = matrix[0].length
  const count = m * n
  const result = []
  let offset = 1
  let loop = Math.floor(count / 2)

  if (m === 1) {
    return matrix[0]
  }
  if (n === 1) {
    return matrix.map((item) => item[0])
  }

  while (loop--) {
    let row = startX
    let col = startY

    for (; col < startY + n - offset; col++) {
      result.push(matrix[row][col])
      if (result.length === count) {
        return result
      }
    }

    for (; row < startX + m - offset; row++) {
      result.push(matrix[row][col])
      if (result.length === count) {
        return result
      }
    }

    for (; col > startY; col--) {
      result.push(matrix[row][col])
      if (result.length === count) {
        return result
      }
    }

    for (; row > startX; row--) {
      result.push(matrix[row][col])
      if (result.length === count) {
        return result
      }
    }

    startX++
    startY++
    offset += 2
  }

  if (count % 2) {
    const midX = Math.floor(m / 2)
    const midY = Math.floor(n / 2)
    result.push(matrix[midX][midY])
  }

  return result
}
```
