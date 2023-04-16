# 有效的字母异位词

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/valid-anagram

## 题目

给定两个字符串`s`和`t`，编写一个函数来判断`t`是否是`s`的字母异位词。

**注意：** 若`s`和`t`中每个字符出现的次数都相同，则称`s`和`t`互为字母异位词。

### 示例

#### 示例 1：

```
输入: s = "anagram", t = "nagaram"
输出: true
```

#### 示例 2：

```
输入: s = "rat", t = "car"
输出: false
```

## 解法

### 哈希表

```javascript
const isAnagram = function (s, t) {
  if (s.length !== t.length) {
    return false
  }

  let map = new Map()

  for (let i = 0; i < s.length; i++) {
    map.set(s[i], map.has(s[i]) ? map.get(s[i]) + 1 : 1)
    map.set(t[i], map.has(t[i]) ? map.get(t[i]) - 1 : -1)
  }

  for (const i of map.values()) {
    if (i !== 0) {
      return false
    }
  }

  return true
}
```
