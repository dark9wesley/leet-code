# 最长重复子数组

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/maximum-length-of-repeated-subarray

## 题目

给两个整数数组 `nums1` 和 `nums2` ，返回 两个数组中 **公共的** 、长度最长的子数组的长度 。

### 示例

#### 示例 1：

```
输入：nums1 = [1,2,3,2,1], nums2 = [3,2,1,4,7]
输出：3
解释：长度最长的公共子数组是 [3,2,1] 。
```

#### 示例 2：

```
输入：nums1 = [0,0,0,0,0], nums2 = [0,0,0,0,0]
输出：5
```

## 解法

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var findLength = function (nums1, nums2) {
  const [m, n] = [nums1.length, nums2.length]

  const dp = new Array(m + 1).fill(0).map(() => new Array(n + 1).fill(0))

  let res = 0

  for (let i = 1; i <= m; i++) {
    for (let j = 1; j <= n; j++) {
      if (nums1[i - 1] === nums2[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1] + 1
      }
      res = Math.max(dp[i][j], res)
    }
  }

  return res
}
```
