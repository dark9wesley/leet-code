# 找到字符串中所有字母异位词

> 难度：中等
>
> 次数：2
>
> https://leetcode.cn/problems/find-all-anagrams-in-a-string

## 题目

给定两个字符串`s`和`p`，找到`s`中所有`p`的**异位词**的子串，返回这些子串的起始索引。不考虑答案输出的顺序。

**异位词**指由相同字母重排列形成的字符串（包括相同的字符串）。

### 示例

#### 示例 1：

```
输入: s = "cbaebabacd", p = "abc"
输出: [0,6]
解释:
起始索引等于 0 的子串是 "cba", 它是 "abc" 的异位词。
起始索引等于 6 的子串是 "bac", 它是 "abc" 的异位词。
```

#### 示例 2：

```
输入: s = "abab", p = "ab"
输出: [0,1,2]
解释:
起始索引等于 0 的子串是 "ab", 它是 "ab" 的异位词。
起始索引等于 1 的子串是 "ba", 它是 "ab" 的异位词。
起始索引等于 2 的子串是 "ab", 它是 "ab" 的异位词。
```

## 解法

### 滑动窗口+哈希表

```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function (s, p) {
  const ans = []
  const base = 'a'.charCodeAt()
  const pCount = new Array(26).fill(0)

  for (const char of p) {
    pCount[char.charCodeAt() - base]++
  }

  const sCount = new Array(26).fill(0)
  let left = (right = 0)

  while (right < s.length) {
    const rightCode = s[right].charCodeAt() - base
    sCount[rightCode]++
    right++

    while (sCount[rightCode] > pCount[rightCode]) {
      let leftCode = s[left].charCodeAt() - base
      sCount[leftCode]--
      left++
    }
    console.log(right, left)
    if (right - left === p.length) {
      ans.push(left)
    }
  }

  return ans
}
```
