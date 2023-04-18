# 两个数组的交集 II

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/intersection-of-two-arrays-ii

## 题目

给你两个整数数组`nums1`和`nums2`，请你以数组形式返回两数组的交集。返回结果中每个元素出现的次数，应与元素在两个数组中都出现的次数一致（如果出现次数不一致，则考虑取较小值）。可以不考虑输出结果的顺序。

### 示例

#### 示例 1：

```
输入：nums1 = [1,2,2,1], nums2 = [2,2]
输出：[2,2]
```

#### 示例 2：

```
输入：nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出：[4,9]
```

## 解法

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
const intersect = function (nums1, nums2) {
  const map = new Map()
  const result = []
  for (const num of nums1) {
    map.set(num, map.has(num) ? map.get(num) + 1 : 1)
  }
  for (const num of nums2) {
    if (map.get(num) > 0) {
      result.push(num)
      map.set(num, map.get(num) - 1)
    }
  }
  return result
}
```
