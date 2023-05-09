# 二叉树的右视图

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/binary-tree-right-side-view

## 题目

给定一个二叉树的 **根节点** `root`，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。

### 示例

#### 示例 1：

![tree](https://assets.leetcode.com/uploads/2021/02/14/tree.jpg)

```
输入: [1,2,3,null,5,null,4]
输出: [1,3,4]
```

#### 示例 2：

```
输入: [1,null,3]
输出: [1,3]
```

#### 示例 3：

```
输入: []
输出: []
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
const rightSideView = function (root) {
  const res = []
  const queue = [root]

  if (!root) {
    return res
  }

  while (queue.length) {
    const { length } = queue
    let cur = null

    for (let i = 0; i < length; i++) {
      const top = queue.shift()
      cur = top.val

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
