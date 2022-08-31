# 将二叉搜索树变平衡

> 难度：中等
>
> https://leetcode.cn/problems/balance-a-binary-search-tree

## 题目

给你一棵二叉搜索树，请你返回一棵  **平衡后**  的二叉搜索树，新生成的树应该与原来的树有着相同的节点值。如果有多种构造方法，请你返回任意一种。

如果一棵二叉搜索树中，每个节点的两棵子树高度差不超过`1`，我们就称这棵二叉搜索树是  **平衡的**。

### 示例

#### 示例 1：

![balance1-tree](https://assets.leetcode.com/uploads/2021/08/10/balance1-tree.jpg)

```
输入：root = [1,null,2,null,3,null,4,null,null]
输出：[2,1,3,null,null,null,4]
解释：这不是唯一的正确答案，[3,1,4,null,2,null,null] 也是一个可行的构造方案。
```

#### 示例 2：

![balanced2-tree](https://assets.leetcode.com/uploads/2021/08/10/balanced2-tree.jpg)

```
输入: root = [2,1,3]
输出: [2,1,3]
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
 * @return {TreeNode}
 */
var balanceBST = function (root) {
  const arr = []
  function inorder(root) {
    if (!root) return

    inorder(root.left)
    arr.push(root.val)
    inorder(root.right)
  }
  inorder(root)

  function buildAVL(low, high) {
    if (low > high) {
      return null
    }

    const mid = Math.floor(low + (high - low) / 2)
    const cur = new TreeNode(arr[mid])
    cur.left = buildAVL(low, mid - 1)
    cur.right = buildAVL(mid + 1, high)
    return cur
  }

  return buildAVL(0, arr.length - 1)
}
```
