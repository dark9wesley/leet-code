# 二叉搜索树节点最小距离

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/minimum-distance-between-bst-nodes

## 题目

给你一个二叉搜索树的根节点 `root` ，返回 **树中任意两不同节点值之间的最小差值** 。

差值是一个正数，其数值等于两值之差的绝对值。

### 示例

#### 示例 1：

![bst1](https://assets.leetcode.com/uploads/2021/02/05/bst1.jpg)

```
输入：root = [4,2,6,1,3]
输出：1
```

#### 示例 2：

![bst2](https://assets.leetcode.com/uploads/2021/02/05/bst2.jpg)

```
输入：root = [1,0,48,null,null,12,49]
输出：1
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
var getMinimumDifference = function (root) {
  let preNode = null,
    diff = Infinity
  const inorder = node => {
    if (!node) {
      return
    }

    inorder(node.right)

    if (preNode && diff > Math.min(diff, preNode.val - node.val)) {
      diff = preNode.val - node.val
    }
    preNode = node
    inorder(node.left)
  }

  inorder(root)
  return diff
}
```
