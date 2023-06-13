# 全排列 II

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/permutations-ii

## 题目

给定一个可包含重复数字的序列 `nums` ，**按任意顺序** 返回所有不重复的全排列。

### 示例

#### 示例 1：

```
输入：nums = [1,1,2]
输出：
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

#### 示例 2：

```
输入：nums = [1,2,3]
输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

## 解法

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permuteUnique = function (nums) {
  const res = [],
    path = []
  const length = nums.length

  const used = new Array(length).fill(0)

  const backTracking = k => {
    if (path.length === length) {
      res.push(path.slice())
      return
    }

    const subUsed = []

    for (let i = 0; i < nums.length; i++) {
      if (subUsed.includes(nums[i]) || used[i] !== 0) {
        continue
      }

      subUsed.push(nums[i])
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
