# 二叉树的所有路径

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/binary-tree-paths

## 题目

给你一个二叉树的根节点 `root` ，按 **任意顺序** ，返回所有从根节点到叶子节点的路
径。

**叶子节点** 是指没有子节点的节点。

### 示例

#### 示例 1：

![paths-tree](https://assets.leetcode.com/uploads/2021/03/12/paths-tree.jpg)

```
输入：root = [1,2,3,null,5]
输出：["1->2->5","1->3"]
```

#### 示例 2：

```
输入：root = [1]
输出：["1"]
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
 * @return {string[]}
 */
var binaryTreePaths = function (root) {
  const res = []
  const getPath = (node, curPath) => {
    if (!node.left && !node.right) {
      curPath += node.val
      res.push(curPath)
      return
    }

    curPath += node.val + '->'
    node.left && getPath(node.left, curPath)
    node.right && getPath(node.right, curPath)
  }

  getPath(root, '')

  return res
}
```
