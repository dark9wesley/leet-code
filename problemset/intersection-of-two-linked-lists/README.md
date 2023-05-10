# 相交链表

> 难度：简单
>
> 次数：2
>
> https://leetcode.cn/problems/intersection-of-two-linked-lists

## 题目

给你两个单链表的头节点`headA`和`headB`，请你找出并返回两个单链表相交的起始节点。
如果两个链表不存在相交节点，返回`null`。

图示两个链表在节点`c1`开始相交：

![160_statement](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_statement.png)

题目数据**保证**整个链式结构中不存在环。

注意，函数返回结果后，链表必须**保持其原始结构**。

### 示例

#### 示例 1：

![160_example_1_1](https://assets.leetcode.com/uploads/2021/03/05/160_example_1_1.png)

```
输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
输出：Intersected at '8'
解释：相交节点的值为 8 （注意，如果两个链表相交则不能为 0）。
从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,6,1,8,4,5]。
在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
— 请注意相交节点的值不为 1，因为在链表 A 和链表 B 之中值为 1 的节点 (A 中第二个节点和 B 中第三个节点) 是不同的节点。换句话说，它们在内存中指向两个不同的位置，而链表 A 和链表 B 中值为 8 的节点 (A 中第三个节点，B 中第四个节点) 在内存中指向相同的位置。
```

#### 示例 2：

![160_example_2](https://assets.leetcode.com/uploads/2021/03/05/160_example_2.png)

```
输入：intersectVal = 2, listA = [1,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
输出：Intersected at '2'
解释：相交节点的值为 2 （注意，如果两个链表相交则不能为 0）。
从各自的表头开始算起，链表 A 为 [1,9,1,2,4]，链表 B 为 [3,2,4]。
在 A 中，相交节点前有 3 个节点；在 B 中，相交节点前有 1 个节点。
```

#### 示例 3：

![160_example_3](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_example_3.png)

```
输入：intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
输出：null
解释：从各自的表头开始算起，链表 A 为 [2,6,4]，链表 B 为 [1,5]。
由于这两个链表不相交，所以 intersectVal 必须为 0，而 skipA 和 skipB 可以是任意值。
这两个链表不相交，因此返回 null 。
```

## 解法

### 暴力解法

```javascript
/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
const getIntersectionNode = function (headA, headB) {
  let curA = headA
  let curB = headB

  while (curA) {
    curA.flag = true
    curA = curA.next
  }

  while (curB) {
    if (curB.flag) {
      return curB
    }
    curB = curB.next
  }

  return null
}
```

### 指针

```javascript
/**
 * @param {ListNode} headA
 * @param {ListNode} headB
 * @return {ListNode}
 */
const getIntersectionNode = function (headA, headB) {
  const getLen = head => {
    let len = 0
    let cur = head
    while (cur) {
      cur = cur.next
      len++
    }
    return len
  }

  let lenA = getLen(headA)
  let lenB = getLen(headB)
  let curA = headA
  let curB = headB

  if (lenA < lenB) {
    // 交换变量注意加 “分号” ，两个数组交换变量在同一个作用域下时
    // 如果不加分号，下面两条代码等同于一条代码: [curA, curB] = [lenB, lenA]
    ;[curA, curB] = [curB, curA]
    ;[lenA, lenB] = [lenB, lenA]
  }

  let diff = lenA - lenB

  while (diff) {
    curA = curA.next
    diff--
  }

  while (curA && curA !== curB) {
    curA = curA.next
    curB = curB.next
  }

  return curA
}
```
