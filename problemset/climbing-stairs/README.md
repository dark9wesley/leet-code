# 爬楼梯

> 难度：简单
>
> https://leetcode.cn/problems/climbing-stairs

## 题目

假设你正在爬楼梯。需要`n`阶你才能到达楼顶。

每次你可以爬`1`或`2`个台阶。你有多少种不同的方法可以爬到楼顶呢？

### 示例

#### 示例 1：

```
输入：n = 2
输出：2
解释：有两种方法可以爬到楼顶。
1. 1 阶 + 1 阶
2. 2 阶
```

#### 示例 2：

```
输入：n = 3
输出：3
解释：有三种方法可以爬到楼顶。
1. 1 阶 + 1 阶 + 1 阶
2. 1 阶 + 2 阶
3. 2 阶 + 1 阶
```

## 解法

### 递归 + 记忆化搜索

```javascript
/**
 * @param {number} n
 * @return {number}
 */
const f = []
var climbStairs = function (n) {
  if (n === 1) {
    return 1
  }

  if (n === 2) {
    return 2
  }

  if (f[n] === undefined) {
    f[n] = climbStairs(n - 1) + climbStairs(n - 2)
  }

  return f[n]
}
```

### 动态规划

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function (n) {
  const f = []
  f[1] = 1
  f[2] = 2
  for (let i = 3; i <= n; i++) {
    f[i] = f[i - 1] + f[i - 2]
  }
  return f[n]
}
```
