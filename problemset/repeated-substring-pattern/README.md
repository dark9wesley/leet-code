# 重复的子字符串

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/repeated-substring-pattern

## 题目

给定一个非空的字符串`s`，检查是否可以通过由它的一个子串重复多次构成。

### 示例

#### 示例 1：

```
输入: s = "abab"
输出: true
解释: 可由子串 "ab" 重复两次构成。
```

#### 示例 2：

```
输入: s = "aba"
输出: false
```

#### 示例 3：

```
输入: s = "abcabcabcabc"
输出: true
解释: 可由子串 "abc" 重复四次构成。 (或子串 "abcabc" 重复两次构成。)
```

## 解法

### 移动匹配

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var repeatedSubstringPattern = function (s) {
  const str = s + s
  return str.substring(1, str.length - 1).includes(s)
}
```

### KMP

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var repeatedSubstringPattern = function (s) {
  if (!s.length) {
    return false
  }

  function getNext(s) {
    let next = []
    let j = 0
    next.push(j)
    for (let i = 1; i < s.length; i++) {
      while (j > 0 && s[i] !== s[j]) {
        j = next[j]
      }
      if (s[i] === s[j]) {
        j++
      }
      next.push(j)
    }
    return next
  }

  let next = getNext(s)
  if (
    next[next.length - 1] !== 0 &&
    s.length % (s.length - next[next.length - 1]) === 0
  ) {
    return true
  }
  return false
}
```
