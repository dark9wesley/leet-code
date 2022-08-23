# 全排列

> 难度：中等
>
> https://leetcode.cn/problems/permutations

## 题目

给定一个不含重复数字的数组`nums`，返回其 所有可能的全排列 。你可以**按任意顺序**返回答案。

### 示例

#### 示例 1：

```
输入：nums = [1,2,3]
输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

#### 示例 2：

```
输入：nums = [0,1]
输出：[[0,1],[1,0]]
```

#### 示例 3：

```
输入：nums = [1]
输出：[[1]]
```

## 解法

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function (nums) {
  const len = nums.length
  const visited = {}
  const cur = []
  const res = []

  const dfs = (nth) => {
    if (nth === len) {
      res.push(cur.slice())
      return
    }

    for (let i = 0; i < len; i++) {
      if (!visited[nums[i]]) {
        visited[nums[i]] = true
        cur.push(nums[i])
        dfs(nth + 1)
        cur.pop()
        delete visited[nums[i]]
      }
    }
  }

  dfs(0)

  return res
}
```
