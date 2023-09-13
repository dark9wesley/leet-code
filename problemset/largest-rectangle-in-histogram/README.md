# 柱状图中最大的矩形

> 难度：困难
>
> 次数：1
>
> https://leetcode.cn/problems/largest-rectangle-in-histogram

## 题目

给定 `n` 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 `1` 。

求在该柱状图中，能够勾勒出来的矩形的最大面积。

### 示例

#### 示例 1：

![histogram](https://assets.leetcode.com/uploads/2021/01/04/histogram.jpg)

```
输入：heights = [2,1,5,6,2,3]
输出：10
解释：最大的矩形为图中红色区域，面积为 10
```

#### 示例 2：

![histogram-1](https://assets.leetcode.com/uploads/2021/01/04/histogram-1.jpg)

```
输入： heights = [2,4]
输出： 4
```

## 解法

### 单调栈

```javascript
/**
 * @param {number[]} heights
 * @return {number}
 */
var largestRectangleArea = function (heights) {
  const stack = []
  heights = [0, ...heights, 0]
  const length = heights.length
  let res = 0

  for (let i = 0; i < length; i++) {
    while (stack.length && heights[i] < heights[stack[stack.length - 1]]) {
      const top = stack.pop()
      const w = i - stack[stack.length - 1] - 1
      const h = heights[top]
      res = Math.max(res, w * h)
    }
    stack.push(i)
  }

  return res
}
```
