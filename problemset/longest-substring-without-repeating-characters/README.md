# 无重复字符的最长子串

> 难度：中等
>
> https://leetcode.cn/problems/longest-substring-without-repeating-characters

## 题目

给定一个字符串 s ，请你找出其中不含有重复字符的**最长子串**的长度。

### 示例

#### 示例 1：

```
输入: s = "abcabcbb"
输出: 3
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

#### 示例 2：

```
输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

#### 示例 3：

```
输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
请注意，你的答案必须是**子串**的长度，"pwke" 是一个子序列，不是子串。
```

## 解法

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function (s) {
  const length = s.length
  let max = 0,
    arr = []
  for (let i = 0; i < length; i++) {
    if (arr.includes(s[i])) {
      arr.splice(0, arr.indexOf(s[i]) + 1)
    }
    arr.push(s[i])
    max = Math.max(max, arr.length)
  }

  return max
}
```
