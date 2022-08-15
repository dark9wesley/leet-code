# 删除排序链表中的重复元素 II

> 难度：中等
>
> https://leetcode.cn/problems/remove-duplicates-from-sorted-list-ii/

## 题目

给定一个已排序的链表的头`head`，删除原始链表中所有重复数字的节点，只留下不同的数字。返回**已排序的链表**。

### 示例

#### 示例 1：

![list1](https://assets.leetcode.com/uploads/2021/01/04/linkedlist1.jpg)

```
输入：head = [1,2,3,3,4,4,5]
输出：[1,2,5]
```

#### 示例 2：

![list2](https://assets.leetcode.com/uploads/2021/01/04/linkedlist2.jpg)

```
输入：head = [1,1,1,2,3]
输出：[2,3]
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
var deleteDuplicates = function (head) {
  if (!head || !head.next) return head
  let dummy = (cur = new ListNode())
  cur.next = head
  while (cur.next && cur.next.next) {
    if (cur.next.val === cur.next.next.val) {
      const val = cur.next.val
      while (cur.next && cur.next.val === val) {
        cur.next = cur.next.next
      }
    } else {
      cur = cur.next
    }
  }

  return dummy.next
}
```
