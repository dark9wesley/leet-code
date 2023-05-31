# 删除二叉搜索树中的节点

> 难度：中等
>
> 次数：2
>
> https://leetcode.cn/problems/delete-node-in-a-bst

## 题目

给定一个二叉搜索树的根节点`root`和一个值`key`，删除二叉搜索树中的`key`对应的节点，并保证二叉搜索树的性质不变。返回二叉搜索树（有可能被更新）的根节点的引用。

一般来说，删除节点可分为两个步骤：

1. 首先找到需要删除的节点；
2. 如果找到了，删除它。

### 示例

#### 示例 1：

![del_node_1](https://assets.leetcode.com/uploads/2020/09/04/del_node_1.jpg)

```
输入：root = [5,3,6,2,4,null,7], key = 3
输出：[5,4,6,2,null,null,7]
解释：给定需要删除的节点值是 3，所以我们首先找到 3 这个节点，然后删除它。
```

#### 示例 2：

```
输入: root = [5,3,6,2,4,null,7], key = 0
输出: [5,3,6,2,4,null,7]
解释: 二叉树不包含值为 0 的节点
```

#### 示例 3：

```
输入: root = [], key = 0
输出: []
```

## 解法

```javascript
/**
 * @param {TreeNode} root
 * @param {number} key
 * @return {TreeNode}
 */
var deleteNode = function (root, key) {
  if (!root) return root

  if (root.val === key) {
    if (!root.left && !root.right) {
      root = null
    } else if (root.left) {
      const maxLeft = findMax(root.left)
      root.val = maxLeft.val
      root.left = deleteNode(root.left, maxLeft.val)
    } else {
      const minRight = findMin(root.right)
      root.val = minRight.val
      root.right = deleteNode(root.right, minRight.val)
    }
  } else if (root.val > key) {
    root.left = deleteNode(root.left, key)
  } else {
    root.right = deleteNode(root.right, key)
  }

  return root
}

function findMax(root) {
  while (root.right) {
    root = root.right
  }
  return root
}

function findMin(root) {
  while (root.left) {
    root = root.left
  }
  return root
}
```
