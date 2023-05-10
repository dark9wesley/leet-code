# 将有序数组转换为二叉搜索树

> 难度：简单
>
> https://leetcode.cn/problems/convert-sorted-array-to-binary-search-tree

## 题目

给你一个整数数组`nums`，其中元素已经按**升序**排列，请你将其转换为一棵**高度平
衡**二叉搜索树。

**高度平衡**二叉树是一棵满足「每个节点的左右两个子树的高度差的绝对值不超过 1 」
的二叉树。

### 示例

#### 示例 1：

![btree1](https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg)

```
输入：nums = [-10,-3,0,5,9]
输出：[0,-3,9,-10,null,5]
```

#### 示例 2：

![btree](https://assets.leetcode.com/uploads/2021/02/18/btree.jpg)

```
输入：nums = [1,3]
输出：[3,1]
```

## 解法

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {number[]} nums
 * @return {TreeNode}
 */
var sortedArrayToBST = function (nums) {
  const len = nums.length

  function buildBST(low, high) {
    if (low > high) {
      return null
    }
    const mid = Math.floor(low + (high - low) / 2)
    const cur = new TreeNode(nums[mid])
    cur.left = buildBST(low, mid - 1)
    cur.right = buildBST(mid + 1, high)
    return cur
  }

  return buildBST(0, len - 1)
}
```
