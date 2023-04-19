# 三数之和

> 难度：中等
>
> 次数：2
>
> https://leetcode.cn/problems/3sum

## 题目

给你一个包含 n 个整数的数组 nums，判断  nums  中是否存在三个元素 a，b，c ，使得  a + b + c = 0 ？请你找出所有和为 0 且不重复的三元组。

注意：答案中不可以包含重复的三元组。

### 示例

#### 示例 1：

```
输入：nums = [-1,0,1,2,-1,-4]
输出：[[-1,-1,2],[-1,0,1]]
```

#### 示例 2：

```
输入：nums = []
输出：[]
```

#### 示例 3：

```
输入：nums = [0]
输出：[]
```

## 解法

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
const threeSum = function (nums) {
  nums.sort((a, b) => a - b)
  const len = nums.length
  const result = []
  for (let i = 0; i < len - 2; i++) {
    if (i > 0 && nums[i] === nums[i - 1]) continue
    let j = i + 1
    let k = len - 1

    while (j < k) {
      const sum = nums[i] + nums[j] + nums[k]
      if (sum > 0) {
        k--
        while (j < k && nums[k] === nums[k + 1]) {
          k--
        }
      } else if (sum < 0) {
        j++
        while (j < k && nums[j] === nums[j - 1]) {
          j++
        }
      } else {
        result.push([nums[i], nums[j], nums[k]])
        j++
        k--
        while (j < k && nums[k] === nums[k + 1]) {
          k--
        }
        while (j < k && nums[j] === nums[j - 1]) {
          j++
        }
      }
    }
  }
  return result
}
```
