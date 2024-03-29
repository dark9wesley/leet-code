# 移动零

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/move-zeroes

## 题目

给定一个数组`nums`，编写一个函数将所有`0`移动到数组的末尾，同时保持非零元素的相对顺序。

**请注意**，必须在不复制数组的情况下原地对数组进行操作。

### 示例

#### 示例 1：

```
输入: nums = [0,1,0,3,12]
输出: [1,3,12,0,0]
```

#### 示例 2：

```
输入: nums = [0]
输出: [0]
```

## 解法

### 双指针

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function (nums) {
  let slow = (fast = 0)
  while (fast < nums.length) {
    if (nums[fast] !== 0) {
      nums[slow] = nums[fast]
      slow++
    }
    fast++
  }

  while (slow < nums.length) {
    nums[slow] = 0
    slow++
  }

  return nums
}
```
