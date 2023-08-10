# 完全平方数

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/perfect-squares

## 题目

给你一个整数 `n` ，返回 **和为** `n` 的完全平方数的最少数量 。

**完全平方数** 是一个整数，其值等于另一个整数的平方；换句话说，其值等于一个整数自乘的积。例如，`1`、`4`、`9` 和 `16` 都是完全平方数，而 `3` 和 `11` 不是。

### 示例

#### 示例 1：

```
输入：n = 12
输出：3
解释：12 = 4 + 4 + 4
```

#### 示例 2：

```
输入：n = 13
输出：2
解释：13 = 4 + 9
```

## 解法

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var numSquares = function (n) {
  const dp = new Array(n + 1).fill(Infinity)

  dp[0] = 0

  for (let i = 1; i ** 2 <= n; i++) {
    const number = i ** 2
    for (let j = number; j < dp.length; j++) {
      dp[j] = Math.min(dp[j], dp[j - number] + 1)
    }
  }

  return dp[n]
}
```
