# 搜索插入位置

> 难度：简单

> 次数：3

> https://leetcode.cn/problems/search-insert-position

## 题目

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

请必须使用时间复杂度为`O(log n)`的算法。

### 示例

#### 示例 1：

```
输入: nums = [1,3,5,6], target = 5
输出: 2
```

#### 示例 2：

```
输入: nums = [1,3,5,6], target = 2
输出: 1
```

#### 示例 3：

```
输入: nums = [1,3,5,6], target = 7
输出: 4
```

## 解法

### 二分查找

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function (nums, target) {
  let i = 0
  let j = nums.length - 1
  while (i <= j) {
    const mid = Math.floor(i + (j - i) / 2)
    if (nums[mid] > target) {
      j = mid - 1
    } else if (nums[mid] < target) {
      i = mid + 1
    } else {
      return mid
    }
  }
  return i
}
```
