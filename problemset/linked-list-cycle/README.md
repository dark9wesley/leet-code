# 环形链表

> 难度：简单
>
> 次数：4
>
> https://leetcode.cn/problems/linked-list-cycle/

## 题目

给你一个链表的头节点`head`，判断链表中是否有环。

如果链表中有某个节点，可以通过连续跟踪`next`指针再次到达，则链表中存在环。 为了表示给定链表中的环，评测系统内部使用整数`pos`来表示链表尾连接到链表中的位置（索引从 0 开始）。**注意：pos 不作为参数进行
传递**。仅仅是为了标识链表的实际情况。

如果链表中存在环  ，则返回`true`。 否则，返回`false`。

### 示例

#### 示例 1：

![circularlinkedlist](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist.png)

```
输入：head = [3,2,0,-4], pos = 1
输出：true
解释：链表中有一个环，其尾部连接到第二个节点。
```

#### 示例 2：

![circularlinkedlist_test2](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test2.png)

```
输入：head = [1,2], pos = 0
输出：true
解释：链表中有一个环，其尾部连接到第一个节点。
```

#### 示例 3：

![circularlinkedlist_test3](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test3.png)

```
输入：head = [1], pos = -1
输出：false
解释：链表中没有环。
```

## 解法

### flag

```javascript
/**
 * @param {ListNode} head
 * @return {boolean}
 */
var hasCycle = function (head) {
  let cur = head
  while (cur) {
    if (cur.flag) {
      return true
    }
    cur.flag = true
    cur = cur.next
  }
  return false
}
```

### 快慢指针

```javascript
/**
 * @param {ListNode} head
 * @return {boolean}
 */
var hasCycle = function (head) {
  if (!head || !head.next) {
    return false
  }

  let slow = head
  let fast = head.next

  while (fast && fast.next && slow !== fast) {
    slow = slow.next
    fast = fast.next.next
  }

  return slow === fast
}
```
