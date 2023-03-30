# 在排序数组中查找元素的第一个和最后一个位置

> 难度：中等

> 次数：2

> https://leetcode.cn/problems/find-first-and-last-position-of-element-in-sorted-array

## 题目

给你一个按照非递减顺序排列的整数数组`nums`，和一个目标值`target`。请你找出给定目标值在数组中的开始位置和结束位置。

如果数组中不存在目标值`target`，返回`[-1, -1]`。

你必须设计并实现时间复杂度为`O(log n)`的算法解决此问题。

### 示例

#### 示例 1：

```
输入：nums = [5,7,7,8,8,10], target = 8
输出：[3,4]
```

#### 示例 2：

```
输入：nums = [5,7,7,8,8,10], target = 6
输出：[-1,-1]
```

#### 示例 3：

```
输入：nums = [], target = 0
输出：[-1,-1]
```

## 解法

### 二分查找

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function (nums, target) {
  const searchLeftBorder = (nums, target) => {
    let leftBorder = -2
    let i = 0
    let j = nums.length - 1
    while (i <= j) {
      const mid = Math.floor(i + (j - i) / 2)
      if (nums[mid] < target) {
        i = mid + 1
      } else {
        j = mid - 1
        leftBorder = j
      }
    }
    return leftBorder
  }
  const searchRightBorder = (nums, target) => {
    let rightBorder = -2
    let i = 0
    let j = nums.length - 1
    while (i <= j) {
      const mid = Math.floor(i + (j - i) / 2)
      if (nums[mid] > target) {
        j = mid - 1
      } else {
        i = mid + 1
        rightBorder = i
      }
    }
    return rightBorder
  }

  const left = searchLeftBorder(nums, target)
  const right = searchRightBorder(nums, target)

  if (left === -2 || right === -2) return [-1, -1]
  if (right - left > 1) return [left + 1, right - 1]

  return [-1, -1]
}
```

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function (nums, target) {
  const left = findBound(nums, target, true)
  const right = findBound(nums, target, false)

  return [left, right]
}

function findBound(nums, target, isFirst) {
  let l = 0,
    r = nums.length - 1,
    result = -1
  while (l <= r) {
    const mid = Math.floor((l + r) / 2)
    if (nums[mid] > target) {
      r = mid - 1
    } else if (nums[mid] < target) {
      l = mid + 1
    } else {
      result = mid
      if (isFirst) {
        r = mid - 1
      } else {
        l = mid + 1
      }
    }
  }

  return result
}
```
