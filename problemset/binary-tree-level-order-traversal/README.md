# 二叉树的层序遍历

> 难度：中等
>
> 次数: 2
>
> https://leetcode.cn/problems/binary-tree-level-order-traversal

## 题目

给你二叉树的根节点`root`，返回它节点值的**层序遍历**。 （即逐层地，从左到右访问所有节点）。

### 示例

#### 示例 1：

![tree1](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)

```
输入：root = [3,9,20,null,null,15,7]
输出：[[3],[9,20],[15,7]]
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
var levelOrder = function (root) {
  const res = []
  const queue = []

  if (!root) return res

  queue.push(root)

  while (queue.length) {
    const len = queue.length
    const cur = []

    for (let i = 0; i < len; i++) {
      const top = queue.shift()
      cur.push(top.val)

      if (top.left) {
        queue.push(top.left)
      }

      if (top.right) {
        queue.push(top.right)
      }
    }

    res.push(cur)
  }

  return res
}
```
