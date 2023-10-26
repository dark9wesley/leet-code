# 剑指 Offer 05. 替换空格

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/ti-huan-kong-ge-lcof

## 题目

请实现一个函数，把字符串`s`中的每个空格替换成"%20"。

## 示例

```
输入：s = "We are happy."
输出："We%20are%20happy."
```

## 解法

### 双指针

```javascript
var replaceSpace = function (s) {
  let strArr = Array.from(s)
  let count = 0

  for (let i = 0; i < strArr.length; i++) {
    if (strArr[i] === ' ') {
      count++
    }
  }

  let left = strArr.length - 1
  let right = strArr.length + count * 2 - 1

  while (left >= 0) {
    if (strArr[left] === ' ') {
      strArr[right--] = '0'
      strArr[right--] = '2'
      strArr[right--] = '%'
      left--
    } else {
      strArr[right--] = strArr[left--]
    }
  }

  return strArr.join('')
}
```

### 正则

```javascript
var replaceSpace = function (s) {
  return s.replace(/ /g, '%20')
}
```

### split + join

```javascript
var replaceSpace = function (s) {
  return s.split(' ').join('%20')
}
```
