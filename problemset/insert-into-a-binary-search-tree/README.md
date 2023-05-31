# 二叉搜索树中的插入操作

> 难度：中等
>
> 次数：2
>
> https://leetcode.cn/problems/insert-into-a-binary-search-tree

## 题目

给定二叉搜索树（BST）的根节点`root`和要插入树中的值`value`，将值插入二叉搜索树。返回插入后二叉搜索树的根节点。 输入数据**保证**，新值和原始二叉搜索树中的任意节点值都不同。

**注意**，可能存在多种有效的插入方式，只要树在插入后仍保持为二叉搜索树即可。 你可以返回**任意有效的结果**。

### 示例

#### 示例 1：

![insertbst](https://assets.leetcode.com/uploads/2020/10/05/insertbst.jpg)

```
输入：root = [4,2,7,1,3], val = 5
输出：[4,2,7,1,3,5]
```

#### 示例 2：

```
输入：root = [40,20,60,10,30,50,70], val = 25
输出：[40,20,60,10,30,50,70,null,null,25]
```

#### 示例 3：

```
输入：root = [4,2,7,1,3,null,null,null,null,null,null], val = 5
输出：[4,2,7,1,3,5]
```

## 解法

### 递归

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
var insertIntoBST = function (root, val) {
  if (!root) {
    root = new TreeNode(val)
    return root
  }

  if (root.val > val) {
    root.left = insertIntoBST(root.left, val)
  } else if (root.val < val) {
    root.right = insertIntoBST(root.right, val)
  }

  return root
}
```

### 迭代

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
var insertIntoBST = function (root, val) {
  if (!root) {
    return new TreeNode(val)
  }

  let cur = root
  let parent = null
  while (cur) {
    parent = cur
    if (cur.val > val) {
      cur = cur.left
    } else if (cur.val < val) {
      cur = cur.right
    }
  }

  if (parent.val > val) {
    parent.left = new TreeNode(val)
  } else if (parent.val < val) {
    parent.right = new TreeNode(val)
  }

  return root
}
```
