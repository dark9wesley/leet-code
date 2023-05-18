# 找树左下角的值

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/find-bottom-left-tree-value

## 题目

给定一个二叉树的 **根节点** `root`，请找出该二叉树的 **最底层** **最左边** 节点
的值。

假设二叉树中至少有一个节点。

### 示例

#### 示例 1：

![tree1](https://assets.leetcode.com/uploads/2020/12/14/tree1.jpg)

```
输入: root = [2,1,3]
输出: 1
```

#### 示例 2：

![tree2](https://assets.leetcode.com/uploads/2020/12/14/tree2.jpg)

```
输入: [1,2,3,4,null,5,6,null,null,7]
输出: 7
```

## 解法

### 层序遍历

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
var findBottomLeftValue = function (root) {
  const queue = [root]
  let num = 0
  while (queue.length) {
    const length = queue.length
    for (let i = 0; i < length; i++) {
      const top = queue.shift()
      num = top.val
      top.right && queue.push(top.right)
      top.left && queue.push(top.left)
    }
  }
  return num
}
```
