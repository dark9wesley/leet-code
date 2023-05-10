# 赎金信

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/ransom-note

## 题目

给你两个字符串：`ransomNote`和`magazine`，判断`ransomNote`能不能由`magazine`里面
的字符构成。

如果可以，返回`true`；否则返回`false`。

`magazine`中的每个字符只能在`ransomNote`中使用一次。

### 示例

#### 示例 1：

```
输入：ransomNote = "a", magazine = "b"
输出：false
```

#### 示例 2：

```
输入：ransomNote = "aa", magazine = "ab"
输出：false
```

#### 示例 3：

```
输入：ransomNote = "aa", magazine = "aab"
输出：true
```

## 解法

### 哈希表

```javascript
/**
 * @param {string} ransomNote
 * @param {string} magazine
 * @return {boolean}
 */
const canConstruct = function (ransomNote, magazine) {
  const charCount = {}

  for (const char of magazine) {
    charCount[char] = charCount[char] ? charCount[char] + 1 : 1
  }

  for (const char of ransomNote) {
    if (!charCount[char]) {
      return false
    }
    charCount[char]--
  }

  return true
}
```
