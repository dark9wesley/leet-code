# 数组中的第 K 个最大元素

> 难度：中等
>
> https://leetcode.cn/problems/kth-largest-element-in-an-array

## 题目

给定整数数组`nums`和整数`k`，请返回数组中第`k`个最大的元素。

请注意，你需要找的是数组排序后的第`k`个最大的元素，而不是第`k`个不同的元素。

你必须设计并实现时间复杂度为`O(n)`的算法解决此问题。

### 示例

#### 示例 1：

```
输入: [3,2,1,5,6,4], k = 2
输出: 5
```

#### 示例 2：

```
输入: [3,2,3,1,2,4,5,5,6], k = 4
输出: 4
```

## 解法

### 暴力求解

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findKthLargest = function (nums, k) {
  nums.sort((a, b) => b - a)

  return nums[k - 1]
}
```

### 小顶堆

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findKthLargest = function (nums, k) {
  const heap = []

  let n = 0

  function createHeap() {
    for (let i = 0; i < k; i++) {
      insert(nums[i])
    }
  }

  function updateHeap() {
    for (let i = k; i < nums.length; i++) {
      if (nums[i] > heap[0]) {
        heap[0] = nums[i]
        downHeap(0, n)
      }
    }
  }

  function downHeap(low, high) {
    let i = low
    let j = i * 2 + 1
    while (j <= high) {
      if (j + 1 <= high && heap[j + 1] < heap[j]) {
        j = j + 1
      }

      if (heap[i] > heap[j]) {
        let temp = heap[j]
        heap[j] = heap[i]
        heap[i] = temp
        i = j
        j = i * 2 + 1
      } else {
        break
      }
    }
  }

  function upHeap(low, high) {
    let i = high
    let j = Math.floor((i - 1) / 2)

    while (j >= low) {
      if (heap[j] > heap[i]) {
        let temp = heap[j]
        heap[j] = heap[i]
        heap[i] = temp
        i = j
        j = Math.floor((i - 1) / 2)
      } else {
        break
      }
    }
  }

  function insert(num) {
    heap[n] = num
    upHeap(0, n)
    n++
  }

  createHeap()

  updateHeap()

  return heap[0]
}
```
