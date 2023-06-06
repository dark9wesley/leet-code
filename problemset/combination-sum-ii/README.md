# 组合总和 II

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/combination-sum-ii

## 题目

给定一个候选人编号的集合 `candidates` 和一个目标数 `target` ，找出 `candidates` 中所有可以使数字和为 `target` 的组合。

`candidates` 中的每个数字在每个组合中只能使用 **一次** 。

注意：解集不能包含重复的组合。

### 示例

#### 示例 1：

```
输入: candidates = [10,1,2,7,6,1,5], target = 8,
输出:
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
```

#### 示例 2：

```
输入: candidates = [2,5,2,1,2], target = 5,
输出:
[
[1,2,2],
[5]
]
```

## 解法

```javascript
/**
 * @param {number[]} candidates
 * @param {number} target
 * @return {number[][]}
 */
var combinationSum2 = function (candidates, target) {
  candidates.sort((a, b) => a - b)
  const path = [],
    res = []

  const backTracking = (k, sum) => {
    if (sum === target) {
      res.push(path.slice())
      return
    }

    for (let i = k; i < candidates.length; i++) {
      if (i > k && candidates[i] === candidates[i - 1]) {
        continue
      }
      if (candidates[i] > target - sum) {
        break
      }
      sum += candidates[i]
      path.push(candidates[i])
      backTracking(i + 1, sum)
      sum -= candidates[i]
      path.pop()
    }
  }

  backTracking(0, 0)

  return res
}
```
