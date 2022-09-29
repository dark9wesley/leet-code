# 排序数组

> 难度：中等
>
> https://leetcode.cn/problems/sort-an-array

## 题目

给你一个整数数组`nums`，请你将该数组升序排列。

### 示例

#### 示例 1：

```
输入：nums = [5,2,3,1]
输出：[1,2,3,5]
```

#### 示例 2：

```
输入：nums = [5,1,1,2,0,0]
输出：[0,0,1,1,2,5]
```

## 解法

### 冒泡排序

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function (nums) {
  const len = nums.length
  for (let i = 0; i < len; i++) {
    let flag = true
    for (let j = 0; j < len - i - 1; j++) {
      if (nums[j] > nums[j + 1]) {
        flag = false
        ;[nums[j], nums[j + 1]] = [nums[j + 1], nums[j]]
      }
    }
    if (flag === true) return nums
  }
  return nums
}
```

### 选择排序

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function (nums) {
  let len = nums.length
  for (let i = 0; i < len - 1; i++) {
    let min = i
    for (let j = i; j < len; j++) {
      if (nums[j] < nums[min]) {
        min = j
      }
    }

    if (i !== min) {
      ;[nums[i], nums[min]] = [nums[min], nums[i]]
    }
  }
  return nums
}
```

### 插入排序

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function (nums) {
  let len = nums.length
  for (let i = 1; i < len; i++) {
    let temp = nums[i]
    let j = i
    while (j > 0 && nums[j - 1] > temp) {
      nums[j] = nums[j - 1]
      j--
    }
    nums[j] = temp
  }
  return nums
}
```
