# 零钱兑换

> 难度：中等
>
> 次数：2
>
> https://leetcode.cn/problems/coin-change

## 题目

给你一个整数数组`coins`，表示不同面额的硬币；以及一个整数`amount`，表示总金额。

计算并返回可以凑成总金额所需的**最少的硬币个数**。如果没有任何一种硬币组合能组成总金额，返回 `-1` 。

你可以认为每种硬币的数量是无限的。

### 示例

#### 示例 1：

```
输入：coins = [1, 2, 5], amount = 11
输出：3
解释：11 = 5 + 5 + 1
```

#### 示例 2：

```
输入：coins = [2], amount = 3
输出：-1
```

#### 示例 3：

```
输入：coins = [1], amount = 0
输出：0
```

## 解法

### 动态规划

```javascript
/**
 * @param {number[]} coins
 * @param {number} amount
 * @return {number}
 */
var coinChange = function (coins, amount) {
  const dp = new Array(amount + 1).fill(Infinity)

  dp[0] = 0

  for (let i = 0; i < coins.length; i++) {
    for (let j = coins[i]; j < dp.length; j++) {
      dp[j] = Math.min(dp[j], dp[j - coins[i]] + 1)
    }
  }

  return dp[amount] === Infinity ? -1 : dp[amount]
}
```
