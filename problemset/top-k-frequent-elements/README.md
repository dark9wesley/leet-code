# 前 K 个高频元素

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/top-k-frequent-elements

## 题目

给你一个整数数组`nums`和一个整数`k`，请你返回其中出现频率前`k`高的元素。你可以按**任意顺序**返回答案。

### 示例

#### 示例 1：

```
输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]
```

#### 示例 2：

```
输入: nums = [1], k = 1
输出: [1]
```

## 解法

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
  const map = new Map()
  
  for (const num of nums) {
    map.set(num, (map.get(num) || 0) + 1)
  }

  return Array.from(map.entries()).sort((a, b) => b[1] - a[1]).slice(0, k).map(a => a[0])
}
```
