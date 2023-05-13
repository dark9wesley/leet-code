# 相同的树

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/same-tree

## 题目

给你两棵二叉树的根节点`p`和`q`，编写一个函数来检验这两棵树是否相同。

如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。

### 示例

#### 示例 1：

![ex1](https://assets.leetcode.com/uploads/2020/12/20/ex1.jpg)

```
输入：p = [1,2,3], q = [1,2,3]
输出：true
```

#### 示例 2：

![ex2](https://assets.leetcode.com/uploads/2020/12/20/ex2.jpg)

```
输入：p = [1,2], q = [1,null,2]
输出：false
```

#### 示例 3：

```
输入：p = [1,2,1], q = [1,1,2]
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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {boolean}
 */
var isSameTree = function (p, q) {
  if ((p === null && q !== null) || (q === null && p !== null)) {
    return false
  } else if (p === null && q === null) {
    return true
  } else if (p.val !== q.val) {
    return false
  }

  return isSameTree(p.left, q.left) && isSameTree(p.right, q.right)
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
 * @return {boolean}
 */
var isSymmetric = function (root) {
  const queue = [p, q]

  while (queue.length) {
    const p = queue.shift()
    const q = queue.shift()

    if ((p === null && q !== null) || (q === null && p !== null)) {
      return false
    } else if (p === null && q === null) {
      continue
    } else if (p.val !== q.val) {
      return false
    }

    queue.push(p.left)
    queue.push(q.left)
    queue.push(p.right)
    queue.push(q.right)
  }

  return true
}
```
