# 从中序与后序遍历序列构造二叉树

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/construct-binary-tree-from-inorder-and-postorder-traversal

## 题目

给定两个整数数组 `inorder` 和 `postorder` ，其中 `inorder` 是二叉树的中序遍历， `postorder` 是同一棵树的后序遍历，请你构造并返回这颗 **二叉树** 。

### 示例

#### 示例 1：

![tree](https://assets.leetcode.com/uploads/2021/02/19/tree.jpg)

```
输入：inorder = [9,3,15,20,7], postorder = [9,15,7,20,3]
输出：[3,9,20,null,null,15,7]
```

#### 示例 2：

```
输入：inorder = [-1], postorder = [-1]
输出：[-1]
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
 * @param {number[]} inorder
 * @param {number[]} postorder
 * @return {TreeNode}
 */
var buildTree = function (inorder, postorder) {
  if (!inorder.length) {
    return null
  }
  const mid = postorder.pop()
  const rootIndex = inorder.indexOf(mid)
  const tree = new TreeNode(mid)
  tree.left = buildTree(inorder.slice(0, rootIndex), postorder.slice(0, rootIndex))
  tree.right = buildTree(inorder.slice(rootIndex + 1), postorder.slice(rootIndex))
  return tree
}
```
