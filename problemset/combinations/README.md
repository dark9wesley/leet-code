# 组合

> 难度：中等
>
> https://leetcode.cn/problems/combinations

## 题目

给定两个整数`n`和`k`，返回范围`[1, n]`中所有可能的`k`个数的组合。

你可以按**任何顺序**返回答案。

### 示例

#### 示例 1：

```
输入：n = 4, k = 2
输出：
[
⁠ [2,4],
⁠ [3,4],
 [2,3],
 [1,2],
⁠ [1,3],
 [1,4],
]
```

#### 示例 2：

```
输入：n = 1, k = 1
输出：[[1]]
```

## 解法

```javascript
/**
 * @param {number} n
 * @param {number} k
 * @return {number[][]}
 */
var combine = function (n, k) {
  const res = []
  const cur = []

  const dfs = nth => {
    if (cur.length === k) {
      res.push(cur.slice())
      return
    }

    for (let i = nth; i <= n; i++) {
      cur.push(i)
      dfs(i + 1)
      cur.pop()
    }
  }

  dfs(1)

  return res
}
```
