# 最长回文子序列

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/longest-palindromic-subsequence

## 题目

给你一个字符串 `s` ，找出其中最长的回文子序列，并返回该序列的长度。

子序列定义为：不改变剩余字符顺序的情况下，删除某些字符或者不删除任何字符形成的一个序列。

### 示例

#### 示例 1：

```
输入：s = "bbbab"
输出：4
解释：一个可能的最长回文子序列为 "bbbb" 。
```

#### 示例 2：

```
输入：s = "cbbd"
输出：2
解释：一个可能的最长回文子序列为 "bb" 。
```

## 解法

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var longestPalindromeSubseq = function (s) {
  const length = s.length
  const dp = Array.from(Array(length), () => Array(length).fill(0))

  for (let i = 0; i < length; i++) {
    dp[i][i] = 1
  }

  for (let i = length - 1; i >= 0; i--) {
    for (let j = i + 1; j < length; j++) {
      if (s[i] === s[j]) {
        dp[i][j] = dp[i + 1][j - 1] + 2
      } else {
        dp[i][j] = Math.max(dp[i + 1][j], dp[i][j - 1])
      }
    }
  }

  return dp[0][length - 1]
}
```
