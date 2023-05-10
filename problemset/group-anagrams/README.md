# 字母异位词分组

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/group-anagrams

## 题目

给你一个字符串数组，请你将**字母异位词**组合在一起。可以按任意顺序返回结果列表。

**字母异位词**是由重新排列源单词的字母得到的一个新单词，所有源单词中的字母通常恰
好只用一次。

### 示例

#### 示例 1：

```
输入: strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
输出: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

#### 示例 2：

```
输入: strs = [""]
输出: [[""]]
```

#### 示例 3：

```
输入: strs = ["a"]
输出: [["a"]]
```

## 解法

### 哈希表

```javascript
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
const groupAnagrams = function (strs) {
  const map = new Map()
  for (const str of strs) {
    const key = str.split('').sort().toString()
    const list = map.has(key) ? map.get(key) : []
    list.push(str)
    map.set(key, list)
  }
  return Array.from(map.values())
}
```
