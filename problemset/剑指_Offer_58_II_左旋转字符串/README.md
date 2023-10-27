# 剑指 Offer 58 - II. 左旋转字符串

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof

## 题目

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字 2，该函数将返回左旋转两位得到的结果"cdefgab"。

## 示例

### 示例 1

```
输入: s = "abcdefg", k = 2
输出: "cdefgab"
```

### 示例 2

```
输入: s = "lrloseumgh", k = 6
输出: "umghlrlose"
```

## 解法

### 数组

```javascript
/**
 * @param {string} s
 * @param {number} n
 * @return {string}
 */
var reverseLeftWords = function (s, n) {
  const strArr = Array.from(s)
  let i = 0
  while (i < n) {
    strArr.push(strArr.shift())
    i++
  }

  return strArr.join('')
}
```

### 速通

```javascript
/**
 * @param {string} s
 * @param {number} n
 * @return {string}
 */
const reverseLeftWords = function (s, n) {
  return s.slice(n, s.length) + s.slice(0, n)
}
```
