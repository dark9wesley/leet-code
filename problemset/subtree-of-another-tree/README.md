# 另一棵树的子树

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/subtree-of-another-tree

## 题目

给你两棵二叉树`root`和`subRoot`。检验`root`中是否包含和`subRoot`具有相同结构和节
点值的子树。如果存在，返回`true`；否则，返回`false`。

二叉树`tree`的一棵子树包括`tree`的某个节点和这个节点的所有后代节点。`tree`也可以
看做它自身的一棵子树。

### 示例

#### 示例 1：

![subtree1-tree](https://assets.leetcode.com/uploads/2021/04/28/subtree1-tree.jpg)

```
输入：root = [3,4,5,1,2], subRoot = [4,1,2]
输出：true
```

#### 示例 2：

![subtree2-tree](https://assets.leetcode.com/uploads/2021/04/28/subtree2-tree.jpg)

```
输入：root = [3,4,5,1,2,null,null,null,null,0], subRoot = [4,1,2]
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
 * @param {TreeNode} subRoot
 * @return {boolean}
 */
var isSubtree = function (root, subRoot) {
  const compare = (left, right) => {
    if (!left && !right) {
      return true
    }

    if (!left || !right || left.val !== right.val) {
      return false
    }

    return compare(left.left, right.left) && compare(left.right, right.right)
  }

  if (!root) {
    return false
  }

  if (compare(root, subRoot)) {
    return true
  }

  return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot)
}
```
