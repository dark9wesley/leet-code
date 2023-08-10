# 单词拆分

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/word-break

## 题目

给你一个字符串 `s` 和一个字符串列表 `wordDict` 作为字典。请你判断是否可以利用字典中出现的单词拼接出 `s` 。

注意：不要求字典中出现的单词全部都使用，并且字典中的单词可以重复使用。

### 示例

#### 示例 1：

```
输入: s = "applepenapple", wordDict = ["apple", "pen"]
输出: true
解释: 返回 true 因为 "applepenapple" 可以由 "apple" "pen" "apple" 拼接成。
注意，你可以重复使用字典中的单词。
```

#### 示例 2：

```
输入: s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]
输出: false
```

## 解法

```javascript
/**
 * @param {string} s
 * @param {string[]} wordDict
 * @return {boolean}
 */
var wordBreak = function (s, wordDict) {
  const dp = new Array(s.length + 1).fill(false)

  dp[0] = true

  for (let i = 0; i < dp.length; i++) {
    for (let j = 0; j < wordDict.length; j++) {
      const word = wordDict[j]
      if (i >= word.length) {
        const subStr = s.slice(i - word.length, i)
        if (subStr === word && dp[i - word.length]) {
          dp[i] = true
        }
      }
    }
  }

  return dp[s.length]
}
```
