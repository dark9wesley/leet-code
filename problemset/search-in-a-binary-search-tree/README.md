# 二叉搜索树中的搜索

> 难度：简单
>
> https://leetcode.cn/problems/search-in-a-binary-search-tree

## 题目

给定二叉搜索树（BST）的根节点`root`和一个整数值`val`。

你需要在 BST 中找到节点值等于`val`的节点。 返回以该节点为根的子树。 如果节点不存
在，则返回`null`。

### 示例

#### 示例 1：

![tree1](https://assets.leetcode.com/uploads/2021/01/12/tree1.jpg)

```
输入：root = [4,2,7,1,3], val = 2
输出：[2,1,3]
```

#### 示例 2：

![tree2](https://assets.leetcode.com/uploads/2021/01/12/tree2.jpg)

```
输入：root = [4,2,7,1,3], val = 5
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
 * @param {number} val
 * @return {TreeNode}
 */
var searchBST = function (root, val) {
  if (!root) return null

  if (val === root.val) {
    return root
  } else if (val > root.val) {
    return searchBST(root.right, val)
  } else if (val < root.val) {
    return searchBST(root.left, val)
  }
}
```
