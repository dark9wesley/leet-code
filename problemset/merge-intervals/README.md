# 合并区间

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/merge-intervals

## 题目

以数组 `intervals` 表示若干个区间的集合，其中单个区间为 `intervals[i] = [starti, endi]` 。请你合并所有重叠的区间，并返回 **一个不重叠的区间数组，该数组需恰好覆盖输入中的所有区间** 。

### 示例

#### 示例 1：

```
输入：intervals = [[1,3],[2,6],[8,10],[15,18]]
输出：[[1,6],[8,10],[15,18]]
解释：区间 [1,3] 和 [2,6] 重叠, 将它们合并为 [1,6].
```

#### 示例 2：

```
输入：intervals = [[1,4],[4,5]]
输出：[[1,5]]
解释：区间 [1,4] 和 [4,5] 可被视为重叠区间。
```

## 解法

```javascript
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function (intervals) {
  intervals.sort((a, b) => a[0] - b[0])
  let prev = intervals[0]
  let result = []
  for (let i = 0; i < intervals.length; i++) {
    const cur = intervals[i]
    if (cur[0] > prev[1]) {
      result.push(prev)
      prev = cur
    } else {
      prev[1] = Math.max(cur[1], prev[1])
    }
  }
  result.push(prev)
  return result
}
```
