# 反转字符串

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/reverse-string

## 题目

编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组`s`的形式给出。

不要给另外的数组分配额外的空间，你必须原地修改输入数组、使用`O(1)`的额外空间解决这一问题。

### 示例

#### 示例 1：

```
输入：s = ["h","e","l","l","o"]
输出：["o","l","l","e","h"]
```

#### 示例 2：

```
输入：s = ["H","a","n","n","a","h"]
输出：["h","a","n","n","a","H"]
```

## 解法

```javascript
/**
 * @param {character[]} s
 * @return {void} Do not return anything, modify s in-place instead.
 */
const reverseString = function (s) {
  const len = s.length
  let i = 0
  let j = len - 1
  while (i <= j) {
    ;[s[i], s[j]] = [s[j], s[i]]
    i++
    j--
  }
}
```
