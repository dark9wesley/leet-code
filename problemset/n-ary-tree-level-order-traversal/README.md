# N 叉树的层序遍历

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/n-ary-tree-level-order-traversal

## 题目

给定一个 N 叉树，返回其节点值的层序遍历。（即从左到右，逐层遍历）。

树的序列化输入是用层序遍历，每组子节点都由 null 值分隔（参见示例）。

### 示例

#### 示例 1：

![narytreeexample](https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png)

```
输入：root = [1,null,3,2,4,null,5,6]
输出：[[1],[3,2,4],[5,6]]
```

#### 示例 2：

![sample_4_964](https://assets.leetcode.com/uploads/2019/11/08/sample_4_964.png)

```
输入：root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
输出：[[1],[2,3,4,5],[6,7,8,9,10],[11,12,13],[14]]
```

## 解法

```javascript
/**
 * // Definition for a Node.
 * function Node(val,children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */
/**
 * @param {Node|null} root
 * @return {number[][]}
 */
const levelOrder = function (root) {
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
      for (const child of top.children) {
        queue.push(child)
      }
    }

    res.push(cur)
  }

  return res
}
```
