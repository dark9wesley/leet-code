# 回文子串

> 难度：中等

> 次数：1

> https://leetcode.cn/problems/palindromic-substrings

## 题目

给你一个字符串 `s` ，请你统计并返回这个字符串中 **回文子串** 的数目。

**回文字符串** 是正着读和倒过来读一样的字符串。

**子字符串** 是字符串中的由连续字符组成的一个序列。

具有不同开始位置或结束位置的子串，即使是由相同的字符组成，也会被视作不同的子串。

### 示例

#### 示例 1：

```
输入：s = "abc"
输出：3
解释：三个回文子串: "a", "b", "c"
```

#### 示例 2：

```
输入：s = "aaa"
输出：6
解释：6个回文子串: "a", "a", "a", "aa", "aa", "aaa"
```

## 解法

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var countSubstrings = function (s) {
  const length = s.length
  const dp = Array.from(new Array(length), () => new Array(length).fill(false))
  let res = 0

  for (let i = length - 1; i >= 0; i--) {
    for (let j = i; j < length; j++) {
      if (s[j] === s[i]) {
        if (j - i < 2) {
          dp[i][j] = true
        } else {
          dp[i][j] = dp[i + 1][j - 1]
        }
      }
      res += dp[i][j] ? 1 : 0
    }
  }

  return res
}
```
