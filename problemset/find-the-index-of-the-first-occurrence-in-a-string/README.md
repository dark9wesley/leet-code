# 找出字符串中第一个匹配项的下标

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/find-the-index-of-the-first-occurrence-in-a-string

## 题目

给你两个字符串`haystack`和`needle`，请你在`haystack`字符串中找出`needle`字符串的
第一个匹配项的下标（下标从`0`开始）。如果`needle`不是 `haystack`的一部分，则返
回`-1`。

### 示例

#### 示例 1：

```
输入：haystack = "sadbutsad", needle = "sad"
输出：0
解释："sad" 在下标 0 和 6 处匹配。
第一个匹配项的下标是 0 ，所以返回 0 。
```

#### 示例 2：

```
输入：haystack = "leetcode", needle = "leeto"
输出：-1
解释："leeto" 没有在 "leetcode" 中出现，所以返回 -1 。
```

## 解法

### 暴力双重循环

```javascript
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
const strStr = function (haystack, needle) {
  for (let i = 0; i < haystack.length; i++) {
    let k = i
    let j = 0
    while (j < needle.length && haystack[k] === needle[j]) {
      k++
      j++
    }
    if (j === needle.length) {
      return i
    }
  }

  return -1
}
```

### KMP 算法

```javascript
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
const strStr = function (haystack, needle) {
  if (needle.length === 0) {
    return 0
  }

  function getNext(needle) {
    const next = []
    let j = 0
    next.push(j)

    for (let i = 1; i < needle.length; i++) {
      while (j > 0 && needle[i] !== needle[j]) {
        j = next[j - 1]
      }
      if (needle[i] === needle[j]) {
        j++
      }
      next.push(j)
    }

    return next
  }

  const next = getNext(needle)
  let j = 0
  for (let i = 0; i < haystack.length; i++) {
    while (j > 0 && haystack[i] !== needle[j]) {
      j = next[j - 1]
    }
    if (haystack[i] === needle[j]) {
      j++
    }
    if (j === needle.length) {
      return i - needle.length + 1
    }
  }

  return -1
}
```
