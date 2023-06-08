# 子集 II

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/subsets-ii

## 题目

给你一个整数数组 `nums` ，其中可能包含重复元素，请你返回该数组所有可能的子集（幂集）。

解集 **不能** 包含重复的子集。返回的解集中，子集可以按 **任意顺序** 排列。

### 示例

#### 示例 1：

```
输入：nums = [1,2,2]
输出：[[],[1],[1,2],[1,2,2],[2],[2,2]]
```

#### 示例 2：

```
输入：nums = [0]
输出：[[],[0]]
```

## 解法

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var subsetsWithDup = function (nums) {
  nums.sort((a, b) => a - b)
  let result = [],
    path = []

  const backTracking = k => {
    result.push(path.slice())

    for (let i = k; i < nums.length; i++) {
      if (i > k && nums[i] === nums[i - 1]) {
        continue
      }
      path.push(nums[i])
      backTracking(i + 1)
      path.pop()
    }
  }

  backTracking(0)

  return result
}
```
