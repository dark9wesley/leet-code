# 有效的括号

> 难度：简单
> 次数：2
> https://leetcode.cn/problems/valid-parentheses

## 题目

给定一个只包括 `'('`，`')'`，`'{'`，`'}'`，`'['`，`']'`  的字符串`s`，判断字符串是否有效。

有效字符串需满足：

1. 左括号必须用相同类型的右括号闭合。
2. 左括号必须以正确的顺序闭合。

### 示例

#### 示例 1：

```
输入：s = "()"
输出：true
```

#### 示例 2：

```
输入：s = "()[]{}"
输出：true
```

#### 示例 3：

```
输入：s = "(]"
输出：false
```

#### 示例 4：

```
输入：s = "([)]"
输出：false
```

#### 示例 5：

```
输入：s = "{[]}"
输出：true
```

## 解法

```javascript
const rightToLeft = {
  '(': ')',
  '{': '}',
  '[': ']',
}

/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function (s) {
  let stack = []
  for (let i = 0; i < s.length; i++) {
    const ch = s[i]
    if (ch === '(' || ch === '{' || ch === '[') {
      stack.push(rightToLeft[ch])
    } else {
      if (ch !== stack.pop()) {
        return false
      }
    }
  }
  return !stack.length
}
```
