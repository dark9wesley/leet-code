# 翻转二叉树

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/invert-binary-tree

## 题目

给你一棵二叉树的根节点`root`，翻转这棵二叉树，并返回其根节点。

### 示例

#### 示例 1：

![invert1-tree](https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg)

```
输入：root = [4,2,7,1,3,6,9]
输出：[4,7,2,9,6,3,1]
```

#### 示例 2：

![invert2-tree](https://assets.leetcode.com/uploads/2021/03/14/invert2-tree.jpg)

```
输入：root = [2,1,3]
输出：[2,3,1]
```

#### 示例 3：

```
输入：root = []
输出：[]
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
 * @return {TreeNode}
 */
var invertTree = function (root) {
  if (!root) return root

  let left = invertTree(root.left)
  let right = invertTree(root.right)

  root.left = right
  root.right = left

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
 * @return {TreeNode}
 */
var invertTree = function (root) {
  if (!root) {
    return root
  }
  const invertNode = root => {
    let left = root.left
    root.left = root.right
    root.right = left
  }

  const stack = [root]

  while (stack.length) {
    const cur = stack.pop()
    invertNode(cur)
    if (cur.right) {
      stack.push(cur.right)
    }
    if (cur.left) {
      stack.push(cur.left)
    }
  }

  return root
}
```
