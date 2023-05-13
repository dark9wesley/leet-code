# 对称二叉树

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/symmetric-tree

## 题目

给你一个二叉树的根节点`root`， 检查它是否轴对称。

### 示例

#### 示例 1：

![symtree1](https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg)

```
输入：root = [1,2,2,3,4,4,3]
输出：true
```

#### 示例 2：

![symtree2](https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg)

```
输入：root = [1,2,2,null,3,null,3]
输出：false
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
 * @return {boolean}
 */
var isSymmetric = function (root) {
  const compare = (left, right) => {
    if (
      (left !== null && right === null) ||
      (right !== null && left === null)
    ) {
      return false
    } else if (left === null && right === null) {
      return true
    }
    if (left.val !== right.val) {
      return false
    }
    return compare(left.left, right.right) && compare(left.right, right.left)
  }
  if (root === null) {
    return true
  }
  return compare(left, right)
}
```
