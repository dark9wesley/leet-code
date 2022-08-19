# 最小栈

> 难度：中等
>
> https://leetcode.cn/problems/min-stack

## 题目

设计一个支持`push`，`pop`，`top`操作，并能在常数时间内检索到最小元素的栈。

实现`MinStack`类:

- `MinStack()` 初始化堆栈对象。
- `void push(int val)`将元素 val 推入堆栈。
- `void pop()`删除堆栈顶部的元素。
- `int top()`获取堆栈顶部的元素。
- `int getMin()`获取堆栈中的最小元素。

### 示例

```
输入：
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

输出：
[null,null,null,null,-3,null,0,-2]

解释：
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.getMin();   --> 返回 -2.
```

## 解法

```javascript
var MinStack = function () {
  this.stack = []
  this.min = Infinity
}

/**
 * @param {number} val
 * @return {void}
 */
MinStack.prototype.push = function (val) {
  if (val < this.min) {
    this.min = val
  }
  this.stack.push(val)
}

/**
 * @return {void}
 */
MinStack.prototype.pop = function () {
  const pop = this.stack.pop()
  if (pop === this.min) {
    let min = Infinity
    for (let i = 0; i < this.stack.length; i++) {
      if (this.stack[i] < min) {
        min = this.stack[i]
      }
    }
    this.min = min
  }
}

/**
 * @return {number}
 */
MinStack.prototype.top = function () {
  if (!this.stack || !this.stack.length) {
    return
  }
  return this.stack[this.stack.length - 1]
}

/**
 * @return {number}
 */
MinStack.prototype.getMin = function () {
  return this.min
}
```
