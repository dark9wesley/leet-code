# 完全二叉树的节点个数

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/count-complete-tree-nodes

## 题目

给你一棵 **完全二叉树** 的根节点`root`，求出该树的节点个数。

**完全二叉树** 的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层
节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为
第`h`层，则该层包含`1 ~ 2h`个节点。

### 示例

#### 示例 1：

![complete](https://assets.leetcode.com/uploads/2021/01/14/complete.jpg)

```
输入：root = [1,2,3,4,5,6]
输出：6
```

#### 示例 2：

```
输入：root = []
输出：0
```

#### 示例 3：

```
输入：root = [1]
输出：1
```

## 解法

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
 * @return {number}
 */
var countNodes = function (root) {
  let num = 0
  if (!root) {
    return num
  }
  const stack = [root]
  while (stack.length) {
    const length = stack.length
    for (let i = 0; i < length; i++) {
      num++
      const top = stack.pop()
      top.left && stack.push(top.left)
      top.right && stack.push(top.right)
    }
  }
  return num
}
```
