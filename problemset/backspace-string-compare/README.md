# 比较含退格的字符串

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/backspace-string-compare

## 题目

给定`s`和`t`两个字符串，当它们分别被输入到空白的文本编辑器后，如果两者相等，返回`true`。`#`代表退格字符。

**注意:** 如果对空文本输入退格字符，文本继续为空。

### 示例

#### 示例 1：

```
输入：s = "ab#c", t = "ad#c"
输出：true
解释：s 和 t 都会变成 "ac"。
```

#### 示例 2：

```
输入：s = "ab##", t = "c#d#"
输出：true
解释：s 和 t 都会变成 ""。
```

#### 示例 3：

```
输入：s = "a#c", t = "b"
输出：false
解释：s 会变成 "c"，但 t 仍然是 "b"。
```

## 解法

### 双指针

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var backspaceCompare = function(s, t) {
  let i = s.length - 1
  let j = t.length - 1
  let skipI = 0
  let skipJ = 0

  while (i >= 0 || j >= 0) {
    while (i >= 0) {
      if (s[i] === '#') {
        i--
        skipI++
      } else if (skipI > 0){
        i--
        skipI--
      } else break
    }

    while (j >= 0) {
      if (t[j] === '#') {
        j--
        skipJ++
      } else if (skipJ > 0){
        j--
        skipJ--
      } else break
    }

    if (s[i] !== t[j]) {
      return false
    }

    i--
    j--
  }

  return true
};
```
