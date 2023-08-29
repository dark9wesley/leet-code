# 两个字符串的删除操作

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/delete-operation-for-two-strings

## 题目

给定两个单词  `word1`  和  `word2` ，返回使得  `word1`  和   `word2`  相同所需的最小步数。

每步  **可以删除任意一个字符串中的一个字符**。

### 示例

#### 示例 1：

```
输入: word1 = "sea", word2 = "eat"
输出: 2
解释: 第一步将 "sea" 变为 "ea" ，第二步将 "eat "变为 "ea"
```

#### 示例 2：

```
输入：word1 = "leetcode", word2 = "etco"
输出：4
```

## 解法

```javascript
/**
 * @param {string} word1
 * @param {string} word2
 * @return {number}
 */
var minDistance = function (word1, word2) {
  const [m, n] = [word1.length, word2.length]

  const dp = new Array(m + 1).fill().map(() => new Array(n + 1).fill(0))

  for (let i = 1; i <= m; i++) {
    dp[i][0] = i
  }

  for (let i = 1; i <= n; i++) {
    dp[0][i] = i
  }

  for (let i = 1; i <= m; i++) {
    for (let j = 1; j <= n; j++) {
      if (word1[i - 1] === word2[j - 1]) {
        dp[i][j] = dp[i - 1][j - 1]
      } else {
        dp[i][j] = Math.min(dp[i][j - 1] + 1, dp[i - 1][j] + 1, dp[i - 1][j - 1] + 2)
      }
    }
  }

  return dp[m][n]
}
```
