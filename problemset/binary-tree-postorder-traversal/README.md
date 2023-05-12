# 二叉树的后序遍历

> 难度：简单
>
> 次数：3
>
> https://leetcode.cn/problems/binary-tree-postorder-traversal

## 题目

给你二叉树的根节点`root`，返回它节点值的**后序**遍历。

### 示例

#### 示例 1：

![pre1](https://assets.leetcode.com/uploads/2020/08/28/pre1.jpg)

```
输入：root = [1,null,2,3]
输出：[3,2,1]
```

#### 示例 2：

```
输入：root = []
输出：[]
```

#### 示例 3：

```
输入：root = [1]
输出：[1]
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
 * @return {number[]}
 */
var postorderTraversal = function (root) {
  const res = []

  const dfs = root => {
    if (!root) return
    dfs(root.left)
    dfs(root.right)
    res.push(root.val)
  }

  dfs(root)

  return res
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
 * @return {number[]}
 */
var postorderTraversal = function (root) {
  const res = []
  const stack = []

  if (!root) return res

  stack.push(root)

  while (stack.length) {
    const top = stack.pop()
    res.unshift(top.val)

    if (top.left) {
      stack.push(top.left)
    }

    if (top.right) {
      stack.push(top.right)
    }
  }

  return res
}
```
