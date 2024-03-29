# 二叉树的前序遍历

> 难度：简单
>
> 次数：3
>
> https://leetcode.cn/problems/binary-tree-preorder-traversal

## 题目

给你二叉树的根节点`root`，返回它节点值的**前序**遍历。

### 示例

#### 示例 1：

![inorder_1](https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg)

```
输入：root = [1,null,2,3]
输出：[1,2,3]
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

#### 示例 4：

![inorder_5](https://assets.leetcode.com/uploads/2020/09/15/inorder_5.jpg)

```
输入：root = [1,2]
输出：[1,2]
```

#### 示例 5：

![inorder_4](https://assets.leetcode.com/uploads/2020/09/15/inorder_4.jpg)

```
输入：root = [1,null,2]
输出：[1,2]
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
var preorderTraversal = function (root) {
  const res = []

  const dfs = root => {
    if (!root) {
      return
    }
    res.push(root.val)
    dfs(root.left)
    dfs(root.right)
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
var preorderTraversal = function (root) {
  const res = []
  const stack = []

  if (!root) return res

  stack.push(root)

  while (stack.length) {
    const cur = stack.pop()
    res.push(cur.val)
    if (cur.right) {
      stack.push(cur.right)
    }
    if (cur.left) {
      stack.push(cur.left)
    }
  }
  return res
}
```

### 统一迭代

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
var preorderTraversal = function (root) {
  const res = []
  if (!root) {
    return res
  }
  const stack = [root]

  while (stack.length) {
    const top = stack.pop()
    if (!top) {
      const val = stack.pop().val
      res.push(val)
      continue
    } else {
      top.right && stack.push(top.right)
      top.left && stack.push(top.left)
      stack.push(top)
      stack.push(null)
    }
  }
  return res
}
```
