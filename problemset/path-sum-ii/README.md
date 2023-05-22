# 路径总和 II

> 难度：中等
>
> 次数：2
>
> https://leetcode.cn/problems/path-sum-ii

## 题目

给你二叉树的根节点 `root` 和一个整数目标和 `targetSum` ，找出所有 **从根节点到叶子节点** 路径总和等于给定目标和的路径。

**叶子节点** 是指没有子节点的节点。

### 示例

#### 示例 1：

![pathsumii1](https://assets.leetcode.com/uploads/2021/01/18/pathsumii1.jpg)

```
输入：root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
输出：[[5,4,11,2],[5,8,4,5]]
```

#### 示例 2：

![pathsum2](https://assets.leetcode.com/uploads/2021/01/18/pathsum2.jpg)

```
输入：root = [1,2,3], targetSum = 5
输出：[]
```

#### 示例 3：

```
输入：root = [1,2], targetSum = 0
输出：[]
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
 * @return {number[][]}
 */
var pathSum = function (root, targetSum) {
  const result = []

  const dfs = (node, sum, curArr) => {
    if (!node.left && !node.right && sum === targetSum) {
      result.push(curArr)
    }
    if (!node.left && !node.right) {
      return
    }
    if (node.left) {
      dfs(node.left, sum + node.left.val, curArr.concat([node.left.val]))
    }
    if (node.right) {
      dfs(node.right, sum + node.right.val, curArr.concat([node.right.val]))
    }
  }
  if (!root) {
    return result
  }
  dfs(root, root.val, [root.val])

  return result
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
 * @return {number[][]}
 */
var pathSum = function (root, targetSum) {
  let result = []
  if (!root) {
    return result
  }
  const queue = [
    {
      node: root,
      sum: root.val
    }
  ]
  const curArr = [[root.val]]
  while (queue.length) {
    const { node, sum } = queue.shift()
    const cur = curArr.shift()
    if (!node.left && !node.right && sum === targetSum) {
      result.push([...cur])
    }
    if (node.left) {
      curArr.push([...cur, node.left.val])
      queue.push({
        node: node.left,
        sum: node.left.val + sum
      })
    }
    if (node.right) {
      curArr.push([...cur, node.right.val])
      queue.push({
        node: node.right,
        sum: node.right.val + sum
      })
    }
  }

  return result
}
```
