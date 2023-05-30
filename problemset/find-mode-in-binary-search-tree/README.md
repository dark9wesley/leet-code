# 二叉搜索树中的众数

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/find-mode-in-binary-search-tree

## 题目

给你一个含重复值的二叉搜索树（BST）的根节点 `root` ，找出并返回 `BST` 中的所有 **众数**（即，出现频率最高的元素）。

如果树中有不止一个众数，可以按 **任意顺序** 返回。

假定 `BST` 满足如下定义：

- 结点左子树中所含节点的值 **小于等于** 当前节点的值
- 结点右子树中所含节点的值 **大于等于** 当前节点的值
- 左子树和右子树都是二叉搜索树

### 示例

#### 示例 1：

![mode-tree](https://assets.leetcode.com/uploads/2021/03/11/mode-tree.jpg)

```
输入：root = [1,null,2,2]
输出：[2]
```

#### 示例 2：

```
输入：root = [0]
输出：[0]
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
var findMode = function (root) {
  let count = 0,
    maxCount = 1
  let pre = root,
    res = []
  const travelTree = node => {
    if (!node) {
      return
    }
    travelTree(node.left)
    if (pre.val === node.val) {
      count++
    } else {
      count = 1
    }
    pre = node
    if (count === maxCount) {
      res.push(node.val)
    }
    if (count > maxCount) {
      res = []
      maxCount = count
      res.push(node.val)
    }
    travelTree(node.right)
  }

  travelTree(root)

  return res
}
```
