# 左叶子之和

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/sum-of-left-leaves

## 题目

给定二叉树的根节点 `root` ，返回所有左叶子之和。

### 示例

#### 示例 1：

![leftsum-tree](https://assets.leetcode.com/uploads/2021/04/08/leftsum-tree.jpg)

```
输入: root = [3,9,20,null,null,15,7]
输出: 24
解释: 在这个二叉树中，有两个左叶子，分别是 9 和 15，所以返回 24
```

#### 示例 2：

```
输入: root = [1]
输出: 0
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
var sumOfLeftLeaves = function (root) {
  if (!root) {
    return 0
  }

  const leftVal = sumOfLeftLeaves(root.left)
  const rightVal = sumOfLeftLeaves(root.right)
  let midVal = 0
  if (root.left && !root.left.left && !root.left.right) {
    midVal = root.left.val
  }

  return leftVal + rightVal + midVal
}
```
