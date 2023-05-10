# 二叉树的层平均值

> 难度：简单
>
> 次数：1
>
> https://leetcode.cn/problems/average-of-levels-in-binary-tree

## 题目

给定一个非空二叉树的根节点`root`, 以数组的形式返回每一层节点的平均值。与实际答案
相差`10^-5`以内的答案可以被接受。

### 示例

#### 示例 1：

![avg1-tree](https://assets.leetcode.com/uploads/2021/03/09/avg1-tree.jpg)

```
输入：root = [3,9,20,null,null,15,7]
输出：[3.00000,14.50000,11.00000]
解释：第 0 层的平均值为 3,第 1 层的平均值为 14.5,第 2 层的平均值为 11 。
因此返回 [3, 14.5, 11] 。
```

#### 示例 2：

![avg2-tree](https://assets.leetcode.com/uploads/2021/03/09/avg2-tree.jpg)

```
输入：root = [3,9,20,15,7]
输出：[3.00000,14.50000,11.00000]
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
const averageOfLevels = function (root) {
  const res = []
  const queue = [root]

  if (!root) {
    return res
  }

  while (queue.length) {
    const { length } = queue
    const cur = []

    for (let i = 0; i < length; i++) {
      const top = queue.shift()
      cur.push(top.val)
      if (top.left) {
        queue.push(top.left)
      }
      if (top.right) {
        queue.push(top.right)
      }
    }
    const q = cur.reduce((a, b) => a + b, 0) / cur.length

    res.push(q)
  }

  return res
}
```
