# 分割等和子集

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/partition-equal-subset-sum

## 题目

给你一个 **只包含正整数** 的 **非空** 数组 `nums` 。请你判断是否可以将这个数组分割成两个子集，使得两个子集的元素和相等。

### 示例

#### 示例 1：

```
输入：nums = [1,5,11,5]
输出：true
解释：数组可以分割成 [1, 5, 5] 和 [11] 。
```

#### 示例 2：

```
输入：nums = [1,2,3,5]
输出：false
解释：数组不能分割成两个元素和相等的子集。
```

## 解法

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var canPartition = function (nums) {
  const sum = nums.reduce((a, b) => a + b)
  if (sum % 2 !== 0) {
    return false
  }
  const dp = new Array(sum / 2 + 1).fill(0)
  for (let i = 0; i < nums.length; i++) {
    for (let j = sum / 2; j >= nums[i]; j--) {
      dp[j] = Math.max(dp[j], dp[j - nums[i]] + nums[i])
      if (dp[j] === sum / 2) {
        return true
      }
    }
  }

  return dp[sum / 2] === sum / 2
}
```
