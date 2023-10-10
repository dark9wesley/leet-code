# 有序数组的平方

> 难度：简单

> 次数：2

> https://leetcode.cn/problems/squares-of-a-sorted-array

## 题目

给你一个按**非递减顺序**排序的整数数组`nums`，返回**每个数字的平方**组成的新数组，要求也按**非递减顺序**排序。

### 示例

#### 示例 1：

```
输入：nums = [-4,-1,0,3,10]
输出：[0,1,9,16,100]
解释：平方后，数组变为 [16,1,0,9,100]
排序后，数组变为 [0,1,9,16,100]
```

#### 示例 2：

```
输入：nums = [-7,-3,2,3,11]
输出：[4,9,9,49,121]
```

## 解法

### 双指针

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortedSquares = function (nums) {
  let len = nums.length
  let res = new Array(len)
  let i = 0,
    j = (k = len - 1)
  while (i <= j) {
    const i2 = nums[i] * nums[i]
    const j2 = nums[j] * nums[j]
    if (i2 > j2) {
      res[k--] = i2
      i++
    } else {
      res[k--] = j2
      j--
    }
  }

  return res
}
```
