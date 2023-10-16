# 删除链表的倒数第 N 个结点

> 难度：中等
>
> 次数：3
>
> https://leetcode.cn/problems/remove-nth-node-from-end-of-list/

## 题目

给你一个链表，删除链表的倒数第`n`个结点，并且返回链表的头结点。

### 示例

#### 示例 1：

![remove_ex1](https://assets.leetcode.com/uploads/2020/10/03/remove_ex1.jpg)

```
输入：head = [1,2,3,4,5], n = 2
输出：[1,2,3,5]
```

#### 示例 2：

```
输入：head = [1], n = 1
输出：[]
```

#### 示例 3：

```
输入：head = [1,2], n = 1
输出：[1]
```

## 解法

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
const removeNthFromEnd = function (head, n) {
  const dummy = new ListNode(0, head)
  let prev = (cur = dummy)
  while (n--) {
    cur = cur.next
  }

  while (cur.next) {
    cur = cur.next
    prev = prev.next
  }

  prev.next = prev.next.next

  return dummy.next
}
```
