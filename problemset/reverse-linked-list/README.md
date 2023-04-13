# 反转链表

> 难度：简单
>
> 次数：3
>
> https://leetcode.cn/problems/reverse-linked-list/

## 题目

给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。

### 示例

#### 示例 1：

![rev1ex1](https://assets.leetcode.com/uploads/2021/02/19/rev1ex1.jpg)

```
输入：head = [1,2,3,4,5]
输出：[5,4,3,2,1]
```

#### 示例 2：

![rev1ex2](https://assets.leetcode.com/uploads/2021/02/19/rev1ex2.jpg)

```
输入：head = [1,2]
输出：[2,1]
```

#### 示例 3：

```
输入：head = []
输出：[]
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
 * @return {ListNode}
 */
var reverseList = function (head) {
  let prev = null
  let cur = head
  while (cur) {
    let next = cur.next
    cur.next = prev
    prev = cur
    cur = next
  }

  return prev
}
```
