# 二叉树的中序遍历

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/binary-tree-inorder-traversal

## 题目

给你二叉树的根节点`root`，返回它节点值的**中序**遍历。

### 示例

#### 示例 1：

![pre1](https://assets.leetcode.com/uploads/2020/08/28/pre1.jpg)

```
输入：root = [1,null,2,3]
输出：[1,3,2]
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
var inorderTraversal = function (root) {
  const res = []
  const stack = []

  let cur = root

  while (cur || stack.length) {
    while (cur) {
      stack.push(cur)
      cur = cur.left
    }

    const top = stack.pop()
    res.push(top.val)

    cur = top.right
  }

  return res
}
```
