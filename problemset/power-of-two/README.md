# 2 的幂

> 难度：简单 https://leetcode.cn/problems/power-of-two

## 题目

给你一个整数`n`，请你判断该整数是否是 2 的幂次方。如果是，返回`true`；否则，返
回`false`。

如果存在一个整数`x`使得`n == 2^x`，则认为`n`是 2 的幂次方。

### 示例

#### 示例 1：

```
输入：n = 1
输出：true
解释：2^0 = 1
```

#### 示例 2：

```
输入：n = 16
输出：true
解释：2^4 = 16
```

#### 示例 3：

```
输入：n = 3
输出：false
```

#### 示例 4：

```
输入：n = 4
输出：true
```

#### 示例 5：

```
输入：n = 5
输出：false
```

## 解法

### 常规解法

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfTwo = function (n) {
  if (n <= 0) return false
  while (n > 1) {
    if (n % 2 !== 0) return false
    n /= 2
  }
  return true
}
```

### 位运算

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfTwo = function (n) {
  return n > 0 && (n & (n - 1)) == 0
}
```
