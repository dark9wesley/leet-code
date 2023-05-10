# 有效的完全平方数

> 难度：简单

> 次数：2

> https://leetcode.cn/problems/valid-perfect-square

## 题目

给定一个**正整数**`num`，编写一个函数，如果`num`是一个完全平方数，则返回`true`，
否则返回`false`。

进阶：**不要**使用任何内置的库函数，如`sqrt`。

### 示例

#### 示例 1：

```
输入：num = 16
输出：true
```

#### 示例 2：

```
输入：num = 14
输出：false
```

## 解法

### 二分查找

```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var isPerfectSquare = function (num) {
  let l = 0
  let r = num
  while (l <= r) {
    const mid = Math.ceil((l + r) / 2)
    if (mid * mid === num) {
      return true
    } else if (mid * mid > num) {
      r = mid - 1
    } else {
      l = mid + 1
    }
  }

  return false
}
```
