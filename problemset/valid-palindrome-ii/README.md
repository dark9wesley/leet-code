# 验证回文字符串 Ⅱ

> 难度：简单
>
> https://leetcode.cn/problems/valid-palindrome-ii

## 题目

给定一个非空字符串  s，最多删除一个字符。判断是否能成为回文字符串。

### 示例

#### 示例 1：

```
输入: s = "aba"
输出: true
```

#### 示例 2：

```
输入: s = "abca"
输出: true
解释: 你可以删除c字符。
```

#### 示例 3：

```
输入: s = "abc"
输出: false
```

## 解法

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var validPalindrome = function (s) {
  const len = s.length
  let l = 0
  let r = len - 1

  const isEqual = (st, ed) => {
    while (st < ed) {
      if (s[st] !== s[ed]) return false
      st++
      ed--
    }
    return true
  }

  while (l < r && s[l] === s[r]) {
    l++
    r--
  }

  if (isEqual(l + 1, r)) return true
  if (isEqual(l, r - 1)) return true

  return false
}
```
