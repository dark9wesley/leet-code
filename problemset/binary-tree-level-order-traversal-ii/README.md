# 二叉树的层序遍历 II

> 难度：中等
>
> 次数: 1
>
> https://leetcode.cn/problems/binary-tree-level-order-traversal-ii

## 题目

给你二叉树的根节点`root`，返回其节点值 **自底向上的层序遍历**。 （即按从叶子节点
所在层到根节点所在的层，逐层从左向右遍历）

### 示例

#### 示例 1：

![tree1](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)

```
输入：root = [3,9,20,null,null,15,7]
输出：[[15,7],[9,20],[3]]
```

#### 示例 2：

```
输入：root = [1]
输出：[[1]]
```

#### 示例 3：

```
输入：root = []
输出：[]
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
 * @param {TreeNode} root
 * @return {number[][]}
 */
const levelOrderBottom = function (root) {
  const res = []
  const queue = [root]

  if (!root) {
    return res
  }

  while (queue.length) {
    const { length } = queue
    const cur = []

    for (let i = 0; i < length; i++) {
      const top = queue.shift()
      cur.push(top.val)

      if (top.left) {
        queue.push(top.left)
      }
      if (top.right) {
        queue.push(top.right)
      }
    }
    res.unshift(cur)
  }

  return res
}
```
