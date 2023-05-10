# 四数之和

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/4sum

## 题目

给你一个由`n`个整数组成的数组`nums`，和一个目标值`target`。请你找出并返回满足下
述全部条件且不重复的四元组`[nums[a], nums[b], nums[c], nums[d]]`（若两个四元组元
素一一对应，则认为两个四元组重复）：

- `0 <= a, b, c, d < n`
- `a、b、c`和`d`互不相同
- `nums[a] + nums[b] + nums[c] + nums[d] == target`

你可以按**任意顺序**返回答案 。

### 示例

#### 示例 1：

```
输入：nums = [1,0,-1,0,-2,2], target = 0
输出：[[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
```

#### 示例 2：

```
输入：nums = [2,2,2,2,2], target = 8
输出：[[2,2,2,2]]
```

## 解法

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[][]}
 */
const fourSum = function (nums, target) {
  const len = nums.length
  if (len < 4) return []
  nums.sort((a, b) => a - b)
  const res = []
  for (let i = 0; i < len - 3; i++) {
    if (i > 0 && nums[i] === nums[i - 1]) {
      continue
    }
    for (let j = i + 1; j < len - 2; j++) {
      if (j > i + 1 && nums[j] === nums[j - 1]) {
        continue
      }
      let l = j + 1
      let r = len - 1
      while (l < r) {
        const sum = nums[i] + nums[j] + nums[l] + nums[r]
        if (sum < target) {
          l++
          continue
        }
        if (sum > target) {
          r--
          continue
        }
        res.push([nums[i], nums[j], nums[l], nums[r]])

        while (l < r && nums[l] === nums[++l]);
        while (l < r && nums[r] === nums[--r]);
      }
    }
  }

  return res
}
```
