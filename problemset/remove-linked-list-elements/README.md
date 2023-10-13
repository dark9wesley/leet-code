# 移除链表元素

> 难度：简单
>
> 次数：2
>
> https://leetcode-cn.com/problems/remove-linked-list-elements

## 题目

给你一个链表的头节点`head`和一个整数`val`，请你删除链表中所有满足`Node.val == val`的节点，并返回**新的头节点**。

### 示例

#### 示例 1：

```
输入：head = [1,2,6,3,4,5,6], val = 6
输出：[1,2,3,4,5]
```

#### 示例 2：

```
输入：head = [], val = 1
输出：[]
```

#### 示例 3：

```
输入：head = [7,7,7,7], val = 7
输出：[]
```

## 解法

```typescript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} val
 * @return {ListNode}
 */
const removeElements = function (head, val) {
  const dummy = new ListNode(0, head)
  let cur = dummy

  while (cur.next) {
    if (cur.next.val === val) {
      cur.next = cur.next.next
    } else {
      cur = cur.next
    }
  }

  return dummy.next
}
```
