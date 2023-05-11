# 二叉树的最小深度

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/minimum-depth-of-binary-tree

## 题目

给定一个二叉树，找出其最小深度。

最小深度是从根节点到最近叶子节点的最短路径上的节点数量。

**说明:** 叶子节点是指没有子节点的节点。

### 示例

#### 示例一

![ex_depth](https://assets.leetcode.com/uploads/2020/10/12/ex_depth.jpg)

```
输入：root = [3,9,20,null,null,15,7]
输出：2
```

#### 示例二

```
输入：root = [2,null,3,null,4,null,5,null,6]
输出：5
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
 * @return {number}
 */
var minDepth = function (root) {
  let dep = 0
  if (!root) {
    return dep
  }
  const queue = [root]
  while (queue.length) {
    dep++
    const length = queue.length
    for (let i = 0; i < length; i++) {
      const top = queue.shift()
      if (!top.left && !top.right) {
        return dep
      }
      if (top.left) {
        queue.push(top.left)
      }
      if (top.right) {
        queue.push(top.right)
      }
    }
  }
}
```
