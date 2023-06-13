# 全排列

> 难度：中等
>
> 次数：2
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
  const length = nums.length

  const res = [],
    path = []

  const used = new Array(length).fill(0)

  const backTracking = k => {
    if (path.length === length) {
      res.push(path.slice())
      return
    }

    for (let i = 0; i < nums.length; i++) {
      if (used[i] !== 0) {
        continue
      }
      used[i] = 1
      path.push(nums[i])
      backTracking(k + 1)
      path.pop()
      used[i] = 0
    }
  }

  backTracking(0)

  return res
}
```
