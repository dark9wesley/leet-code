# 二叉树的最大深度

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/maximum-depth-of-binary-tree

## 题目

给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

**说明:** 叶子节点是指没有子节点的节点。

### 示例

给定二叉树 [3,9,20,null,null,15,7]，

```
    3
   / \
  9  20
    /  \
   15   7
```

返回它的最大深度 3 。

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
var maxDepth = function (root) {
  let depth = 0
  if (!root) {
    return depth
  }
  const queue = [root]

  while (queue.length) {
    const length = queue.length
    for (let i = 0; i < length; i++) {
      let cur = queue.shift()
      if (cur.left) {
        queue.push(cur.left)
      }
      if (cur.right) {
        queue.push(cur.right)
      }
    }
    depth++
  }

  return depth
}
```
