# 判断子序列

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/is-subsequence

## 题目

给定字符串 `s` 和 `t` ，判断 `s` 是否为 `t` 的子序列。

字符串的一个子序列是原始字符串删除一些（也可以不删除）字符而不改变剩余字符相对位置形成的新字符串。（例如，`"ace"`是`"abcde"`的一个子序列，而`"aec"`不是）。

### 示例

#### 示例 1：

```
输入：s = "abc", t = "ahbgdc"
输出：true
```

#### 示例 2：

```
输入：s = "axc", t = "ahbgdc"
输出：false
```

## 解法

### 双指针

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isSubsequence = function (s, t) {
  let i = 0,
    j = 0

  while (i < s.length && j < t.length) {
    if (s[i] === t[j]) {
      i++
    }
    j++
  }

  return i >= s.length
}
```

### 动态规划

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
const [m, n] = [s.length, t.length]
const dp = new Array(m + 1).fill().map(() => new Array(n + 1).fill(0))

for (let i = 1; i <= m; i++) {
  for (let j = 1; j <= n; j++) {
    if (s[i - 1] === t[j - 1]) {
      dp[i][j] = dp[i - 1][j - 1] + 1
    } else {
      dp[i][j] = dp[i][j - 1]
    }
  }
}

return dp[m][n] === m
```
