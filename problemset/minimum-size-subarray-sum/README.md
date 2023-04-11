# 长度最小的子数组

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/minimum-size-subarray-sum

## 题目

给定一个含有`n`个正整数的数组和一个正整数`target`。

找出该数组中满足其和`≥ target`的长度最小的**连续子数组** `[numsl, numsl+1, ..., numsr-1, numsr]`，并返回其长度。如果不存在符合条件的子数组，返回`0`。

### 示例

#### 示例 1：

```
输入：target = 7, nums = [2,3,1,2,4,3]
输出：2
解释：子数组 [4,3] 是该条件下的长度最小的子数组。
```

#### 示例 2：

```
输入：target = 4, nums = [1,4,4]
输出：1
```

#### 示例 3：

```
输入：target = 11, nums = [1,1,1,1,1,1,1,1]
输出：0
```

## 解法

### 滑动窗口

```javascript
/**
 * @param {number} target
 * @param {number[]} nums
 * @return {number}
 */
var minSubArrayLen = function(target, nums) {
  let len = nums.length
  let start = end = 0
  let sum = 0
  let ans = Infinity

  while(end < len){
    sum += nums[end]
    while(sum >= target){
      ans = Math.min(ans, end - start + 1)
      sum = sum - nums[start]
      start++
    }
    end++
  }

  return ans === Infinity ? 0 : ans
}
```
