# 用队列实现栈

> 难度：简单
>
> 次数：3
>
> https://leetcode.cn/problems/implement-stack-using-queues

## 题目

请你仅使用两个队列实现一个后入先出（LIFO）的栈，并支持普通栈的全部四种操作（`push`、`top`、`pop` 和 `empty`）。

实现`MyStack`类：

- `void push(int x)`将元素 x 压入栈顶。
- `int pop()`移除并返回栈顶元素。
- `int top()`返回栈顶元素。
- `boolean empty()`如果栈是空的，返回`true`；否则，返回`false`。

**注意：**

- 你只能使用队列的基本操作 —— 也就是 `push to back`、`peek/pop from front`、`size` 和 `is empty`  这些操作。
- 你所使用的语言也许不支持队列。你可以使用 list （列表）或者 deque（双端队列）来模拟一个队列  , 只要是标准的队列操作即可。

### 示例

```
输入：
["MyStack", "push", "push", "top", "pop", "empty"]
[[], [1], [2], [], [], []]
输出：
[null, null, null, 2, 2, false]

解释：
MyStack myStack = new MyStack();
myStack.push(1);
myStack.push(2);
myStack.top(); // 返回 2
myStack.pop(); // 返回 2
myStack.empty(); // 返回 False
```

## 解法

```javascript
var MyStack = function () {
  this.queue = []
}

/**
 * @param {number} x
 * @return {void}
 */
MyStack.prototype.push = function (x) {
  this.queue.push(x)
}

/**
 * @return {number}
 */
MyStack.prototype.pop = function () {
  let size = this.queue.length
  while (size-- > 1) {
    this.queue.push(this.queue.shift())
  }
  return this.queue.shift()
}

/**
 * @return {number}
 */
MyStack.prototype.top = function () {
  let top = this.pop()
  this.queue.push(top)
  return top
}

/**
 * @return {boolean}
 */
MyStack.prototype.empty = function () {
  return !this.queue.length
}

/**
 * Your MyStack object will be instantiated and called as such:
 * var obj = new MyStack()
 * obj.push(x)
 * var param_2 = obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.empty()
 */
```
