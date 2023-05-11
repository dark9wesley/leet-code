# 填充每个节点的下一个右侧节点指针 II

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/populating-next-right-pointers-in-each-node-ii

## 题目

给定一个二叉树：

```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```

填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点
，则将 next 指针设置为`NULL`。

初始状态下，所有 next 指针都被设置为`NULL`。

### 示例

#### 示例 1：

![116_sample](https://assets.leetcode.com/uploads/2019/02/15/117_sample.png)

```
输入：root = [1,2,3,4,5,null,7]
输出：[1,#,2,3,#,4,5,7,#]
解释：给定二叉树如图 A 所示，你的函数应该填充它的每个 next 指针，以指向其下一个右侧节点，如图 B 所示。序列化输出按层序遍历顺序（由 next 指针连接），'#' 表示每层的末尾。
```

#### 示例 2：

```
输入：root = []
输出：[]
```

## 解法

```javascript
/**
 * // Definition for a Node.
 * function Node(val, left, right, next) {
 *    this.val = val === undefined ? null : val;
 *    this.left = left === undefined ? null : left;
 *    this.right = right === undefined ? null : right;
 *    this.next = next === undefined ? null : next;
 * };
 */

/**
 * @param {Node} root
 * @return {Node}
 */
const connect = function (root) {
  if (!root) {
    return root
  }
  let queue = [root]
  while (queue.length) {
    const { length } = queue
    const nextQueue = []
    queue.push(null)
    for (let i = 0; i < length; i++) {
      queue[i].next = queue[i + 1]
      if (queue[i].left) {
        nextQueue.push(queue[i].left)
      }
      if (queue[i].right) {
        nextQueue.push(queue[i].right)
      }
    }
    queue = nextQueue
  }
  return root
}
```
