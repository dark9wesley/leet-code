# 反转字符串 II

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/reverse-string-ii

## 题目

给定一个字符串`s`和一个整数`k`，从字符串开头算起，每计数至`2k`个字符，就反转这`2k`字符中的前`k`个字符。

- 如果剩余字符少于`k`个，则将剩余字符全部反转。
- 如果剩余字符小于`2k`但大于或等于`k`个，则反转前`k`个字符，其余字符保持原样。

### 示例

#### 示例 1：

```
输入：s = "abcdefg", k = 2
输出："bacdfeg"
```

#### 示例 2：

```
输入：s = "abcd", k = 2
输出："bacd"
```

## 解法

```javascript
/**
 * @param {string} s
 * @param {number} k
 * @return {string}
 */
const reverseStr = function (s, k) {
  const len = s.length
  const arr = s.split('')
  for (let i = 0; i < len; i += 2 * k) {
    let l = i - 1
    let r = i + k > len ? len : i + k
    while (++l < --r) {
      ;[arr[l], arr[r]] = [arr[r], arr[l]]
    }
  }
  return arr.join('')
}
```
