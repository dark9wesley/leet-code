# 平衡二叉树

> 难度：简单
>
> https://leetcode.cn/problems/balanced-binary-tree

## 题目

给定一个二叉树，判断它是否是高度平衡的二叉树。

本题中，一棵高度平衡二叉树定义为：

`一个二叉树每个节点的左右两个子树的高度差的绝对值不超过 1 。`

### 示例

#### 示例 1：

![balance_1](https://assets.leetcode.com/uploads/2020/10/06/balance_1.jpg)

```
输入：root = [3,9,20,null,null,15,7]
输出：true
```

#### 示例 2：

![balance_2](https://assets.leetcode.com/uploads/2020/10/06/balance_2.jpg)

```
输入：root = [1,2,2,3,3,null,null,4,4]
输出：false
```

#### 示例 3：

```
输入：root = []
输出：true
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
 * @return {boolean}
 */
var isBalanced = function (root) {
  let flag = true
  const dfs = root => {
    if (!root || !flag) {
      return 0
    }

    const left = dfs(root.left)
    const right = dfs(root.right)

    if (Math.abs(left - right) > 1) {
      flag = false
      return 0
    }

    return Math.max(left, right) + 1
  }

  dfs(root)

  return flag
}
```
