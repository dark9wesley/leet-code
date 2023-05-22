# 路径总和

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/path-sum

## 题目

给你二叉树的根节点 `root` 和一个表示目标和的整数 `targetSum` 。判断该树中是否存在 **根节点到叶子节点** 的路径，这条路径上所有节点值相加等于目标和 `targetSum` 。如果存在，返回 `true` ；否则，返回
`false` 。

**叶子节点** 是指没有子节点的节点。

### 示例

#### 示例 1：

![pathsum1](https://assets.leetcode.com/uploads/2021/01/18/pathsum1.jpg)

```
输入：root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22
输出：true
解释：等于目标和的根节点到叶节点路径如上图所示。
```

#### 示例 2：

![pathsum2](https://assets.leetcode.com/uploads/2021/01/18/pathsum2.jpg)

```
输入：root = [1,2,3], targetSum = 5
输出：false
解释：树中存在两条根节点到叶子节点的路径：
(1 --> 2): 和为 3
(1 --> 3): 和为 4
不存在 sum = 5 的根节点到叶子节点的路径。
```

#### 示例 3：

```
输入：root = [], targetSum = 0
输出：false
解释：由于树是空的，所以不存在根节点到叶子节点的路径。
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
 * @param {number} targetSum
 * @return {boolean}
 */
var hasPathSum = function (root, targetSum) {
  if (!root) {
    return false
  }
  const dfs = (node, curNum) => {
    if (!node.left && !node.right && curNum === 0) {
      return true
    }
    if (!node.left && !node.right) {
      return false
    }

    if (node.left && dfs(node.left, curNum - node.left.val)) {
      return true
    }
    if (node.right && dfs(node.right, curNum - node.right.val)) {
      return true
    }

    return false
  }

  return dfs(root, targetSum - root.val)
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
 * @param {number} targetSum
 * @return {boolean}
 */
var hasPathSum = function (root, targetSum) {
  if (!root) {
    return false
  }

  const queue = [
    {
      node: root,
      val: 0
    }
  ]

  while (queue.length) {
    let { node, val } = queue.shift()
    val += node.val
    if (!node.left && !node.right && val === targetSum) {
      return true
    }

    if (node.left) {
      queue.push({
        node: node.left,
        val
      })
    }
    if (node.right) {
      queue.push({
        node: node.right,
        val
      })
    }
  }

  return false
}
```
