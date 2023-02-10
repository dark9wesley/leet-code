# 二分查找

> 难度：简单
>
> https://leetcode.cn/problems/binary-search

## 题目

给定一个`n`个元素有序的（升序）整型数组`nums`和一个目标值`target`，写一个函数搜索`nums`中的`target`，如果目标值存在返回下标，否则返回`-1`。

### 示例

#### 示例 1：

```
输入: nums = [-1,0,3,5,9,12], target = 9
输出: 4
解释: 9 出现在 nums 中并且下标为 4
```

#### 示例 2：

```
输入: nums = [-1,0,3,5,9,12], target = 2
输出: -1
解释: 2 不存在 nums 中因此返回 -1
```

## 解法

### 二分查找 左闭右闭 (包含左右两个边界)

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function (nums, target) {
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
  return -1
}
```

### 二分查找 左闭右开 (包含左边界，不含右边界)

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function (nums, target) {
  let i = 0
  let j = nums.length
  while (i < j) {
    const mid = Math.floor(i + (j - i) / 2)
    if (nums[mid] > target) {
      j = mid
    } else if (nums[mid] < target) {
      i = mid + 1
    } else {
      return mid
    }
  }
  return -1
}
```
