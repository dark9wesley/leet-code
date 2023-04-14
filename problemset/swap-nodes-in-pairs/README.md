# 两两交换链表中的节点

> 难度：中等
>
> 次数：2
>
> https://leetcode.cn/problems/swap-nodes-in-pairs

## 题目

给你一个链表，两两交换其中相邻的节点，并返回交换后链表的头节点。你必须在不修改节点内部的值的情况下完成本题（即，只能进行节点交换）。

### 示例

#### 示例 1：

```
输入：head = [1,2,3,4]
输出：[2,1,4,3]
```

#### 示例 2：

```
输入：head = []
输出：[]
```

#### 示例 3：

```
输入：head = [1]
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
 * @return {ListNode}
 */
var swapPairs = function (head) {
  let dummy = new ListNode(0, head)
  let temp = dummy
  while (temp.next && temp.next.next) {
    let node1 = temp.next
    let node2 = temp.next.next
    temp.next = node2
    node1.next = node2.next
    node2.next = node1
    temp = node1
  }
  return dummy.next
}
```
