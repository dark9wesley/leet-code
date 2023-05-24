# 从前序与中序遍历序列构造二叉树

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/construct-binary-tree-from-preorder-and-inorder-traversal

## 题目

给定两个整数数组`preorder`和 `inorder` ，其中 `preorder` 是二叉树的先序遍历， `inorder` 是同一棵树的中序遍历，请构造二叉树并返回其根节点。

### 示例

#### 示例 1：

![tree](https://assets.leetcode.com/uploads/2021/02/19/tree.jpg)

```
输入: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
输出: [3,9,20,null,null,15,7]
```

#### 示例 2：

```
输入: preorder = [-1], inorder = [-1]
输出: [-1]
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
var buildTree = function (preorder, inorder) {
  if (!inorder.length) {
    return null
  }
  const mid = preorder.shift()
  const rootIndex = inorder.indexOf(mid)
  const tree = new TreeNode(mid)
  tree.left = buildTree(preorder.slice(0, rootIndex), inorder.slice(0, rootIndex))
  tree.right = buildTree(preorder.slice(rootIndex), inorder.slice(rootIndex + 1))

  return tree
}
```
