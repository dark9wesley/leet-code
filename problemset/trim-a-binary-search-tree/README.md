# 修剪二叉搜索树

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/trim-a-binary-search-tree

## 题目

给你二叉搜索树的根节点 `root` ，同时给定最小边界 `low` 和最大边界 `high`。通过修剪二叉搜索树，使得所有节点的值在`[low, high]`中。修剪树 **不应该** 改变保留在树中的元素的相对结构 (即，如果没有被移除，
原有的父代子代关系都应当保留)。 可以证明，存在 **唯一的答案** 。

所以结果应当返回修剪好的二叉搜索树的新的根节点。注意，根节点可能会根据给定的边界发生改变。

### 示例

#### 示例 1：

![trim1](https://assets.leetcode.com/uploads/2020/09/09/trim1.jpg)

```
输入：root = [1,0,2], low = 1, high = 2
输出：[1,null,2]
```

#### 示例 2：

![trim2](https://assets.leetcode.com/uploads/2020/09/09/trim2.jpg)

```
输入：root = [3,0,4,null,2,null,null,1], low = 1, high = 3
输出：[3,2,null,1]
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
 * @param {number} low
 * @param {number} high
 * @return {TreeNode}
 */
var trimBST = function (root, low, high) {
  if (!root) {
    return root
  }
  const val = root.val
  if (val < low) {
    root = trimBST(root.right, low, high)
  } else if (val > high) {
    root = trimBST(root.left, low, high)
  } else {
    root.left = trimBST(root.left, low, high)
    root.right = trimBST(root.right, low, high)
  }

  return root
}
```
