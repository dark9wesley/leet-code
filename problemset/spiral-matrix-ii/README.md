# 螺旋矩阵 II

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/spiral-matrix-ii

## 题目

给你一个正整数`n`，生成一个包含`1`到`n^2`所有元素，且元素按顺时针顺序螺旋排列的`n x n`正方形矩阵`matrix`。

### 示例

#### 示例 1：

![spiraln](https://assets.leetcode.com/uploads/2020/11/13/spiraln.jpg)

```
输入：n = 3
输出：[[1,2,3],[8,9,4],[7,6,5]]
```

#### 示例 2：

```
输入：n = 1
输出：[[1]]
```

## 解法

### 模拟行为

```javascript
/**
 * @param {number} n
 * @return {number[][]}
 */
const generateMatrix = function (n) {
  let startX = 0
  let startY = 0
  let loop = Math.floor(n / 2)
  const mid = Math.floor(n / 2)
  const result = new Array(n).fill(0).map(() => new Array(n).fill(0))
  let count = 1
  let offset = 1

  while (loop--) {
    let row = startX
    let col = startY
    for (; col < startY + n - offset; col++) {
      result[row][col] = count++
    }

    for (; row < startX + n - offset; row++) {
      result[row][col] = count++
    }

    for (; col > startY; col--) {
      result[row][col] = count++
    }

    for (; row > startX; row--) {
      result[row][col] = count++
    }

    offset += 2
    startX++
    startY++
  }

  if (n % 2 !== 0) {
    result[mid][mid] = count++
  }

  return result
}
```
