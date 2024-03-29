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

冒泡排序的过程，就是从第一个元素开始，**重复比较相邻的两个项**，若第一项比第二项
更大，则交换两者的位置；反之不动。

每一轮操作，都会将这一轮中最大的元素放置到数组的末尾。假如数组的长度是`n`，那么
当我们重复完`n`轮的时候，整个数组就有序了。

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

选择排序的关键字是“**最小值**”：循环遍历数组，每次都找出当前范围内的最小值，把它
放在当前范围的头部；然后缩小排序范围，继续重复以上操作，直至数组完全有序为止。

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

插入排序的核心思想是“找到元素在它前面那个序列中的正确位置”。具体来说，插入排序所
有的操作都基于一个这样的前提：当前元素前面的序列是有序的。基于这个前提，从后往前
去寻找当前元素在前面那个序列里的正确位置。

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

### 归并排序

归并排序是对分治思想的典型应用，它按照如下的思路对分治思想“三步走”的框架进行了填
充：

- **分解子问题**：将需要被排序的数组从中间分割为两半，然后再将分割出来的每个子数
  组各分割为两半，重复以上操作，直到单个子数组只有一个元素为止。
- **求解每个子问题**：从粒度最小的子数组开始，两两合并、确保每次合并出来的数组都
  是有序的。（这里的“子问题”指的就是对每个子数组进行排序）。
- **合并子问题的解，得出大问题的解**：当数组被合并至原有的规模时，就得到了一个完
  全排序的数组

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function (nums) {
  if (nums.length <= 1) {
    return nums
  }
  const len = nums.length
  const mid = Math.floor(len / 2)
  const left = sortArray(nums.slice(0, mid))
  const right = sortArray(nums.slice(mid, len))
  return sortNums(left, right)
}

function sortNums(arr1, arr2) {
  let i = 0
  let j = 0
  let result = []
  const len1 = arr1.length
  const len2 = arr2.length
  while (i < len1 && j < len2) {
    if (arr1[i] < arr2[j]) {
      result.push(arr1[i])
      i++
    } else {
      result.push(arr2[j])
      j++
    }
  }
  if (i < len1) {
    result = result.concat(arr1.slice(i))
  }
  if (j < len2) {
    result = result.concat(arr2.slice(j))
  }

  return result
}
```

### 快速排序

快速排序在基本思想上和归并排序是一致的，仍然坚持“分而治之”的原则不动摇。区别在于
，快速排序并不会把真的数组分割开来再合并到一个新数组中去，而是直接在原有的数组内
部进行排序。

快速排序会将原始的数组筛选成较小和较大的两个子数组，然后递归地排序两个子数组。

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function (nums, left = 0, right = nums.length - 1) {
  if (nums.length > 1) {
    // lineIndex表示下一次划分左右子数组的索引位
    const index = partition(nums, left, right)
    // 如果左边子数组的长度不小于1，则递归快排这个子数组
    if (left < index - 1) {
      // 左子数组以 lineIndex-1 为右边界
      sortArray(nums, left, index - 1)
    }
    // 如果右边子数组的长度不小于1，则递归快排这个子数组
    if (index < right) {
      // 右子数组以 lineIndex 为左边界
      sortArray(nums, index, right)
    }
  }
  return nums
}

function partition(arr, left, right) {
  // 初始化左右指针
  let i = left
  let j = right
  // 基准值默认取中间位置的元素
  let pivotValue = arr[Math.floor(left + (right - left) / 2)]
  // 当左右指针不越界时，循环执行以下逻辑
  while (i <= j) {
    // 左指针所指元素若小于基准值，则右移左指针
    while (arr[i] < pivotValue) {
      i++
    }
    // 右指针所指元素大于基准值，则左移右指针
    while (arr[j] > pivotValue) {
      j--
    }
    // 若i<=j，则意味着基准值左边存在较大元素或右边存在较小元素，交换两个元素确保左右两侧有序
    if (i <= j) {
      ;[arr[i], arr[j]] = [arr[j], arr[i]]
      i++
      j--
    }
  }
  // 返回左指针索引作为下一次划分左右子数组的依据
  return i
}
```
