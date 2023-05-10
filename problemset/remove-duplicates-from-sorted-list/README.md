# 删除排序链表中的重复元素

> 难度：简单
>
> https://leetcode.cn/problems/remove-duplicates-from-sorted-list/

## 题目

给定一个已排序的链表的头`head`，删除所有重复的元素，使每个元素只出现一次。返
回**已排序的链表**。

### 示例

#### 示例 1：

![list1](https://assets.leetcode.com/uploads/2021/01/04/list1.jpg)

```
输入：head = [1,1,2]
输出：[1,2]
```

#### 示例 2：

![list2](https://assets.leetcode.com/uploads/2021/01/04/list2.jpg)

```
输入：head = [1,1,2,3,3]
输出：[1,2,3]
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
  let cur = head
  while (cur !== null && cur.next !== null) {
    if (cur.val === cur.next.val) {
      cur.next = cur.next.next
    } else {
      cur = cur.next
    }
  }
  return head
}
```
