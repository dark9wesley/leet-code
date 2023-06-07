# 分割回文串

> 难度：中等

> 次数：1

> https://leetcode.cn/problems/palindrome-partitioning

## 题目

给你一个字符串 `s`，请你将 `s` 分割成一些子串，使每个子串都是 **回文串** 。返回 `s` 所有可能的分割方案。

**回文串** 是正着读和反着读都一样的字符串。

### 示例

#### 示例 1：

```
输入：s = "aab"
输出：[["a","a","b"],["aa","b"]]
```

#### 示例 2：

```
输入：s = "a"
输出：[["a"]]
```

## 解法

```javascript
/**
 * @param {string} s
 * @return {string[][]}
 */
var partition = function (s) {
  const res = [],
    path = []

  const isPalindrome = str => {
    let i = 0,
      j = str.length - 1
    while (i <= j) {
      if (str[i] !== str[j]) {
        return false
      }
      i++
      j--
    }
    return true
  }

  const backTracking = k => {
    if (k >= s.length) {
      res.push(path.slice())
      return
    }

    for (let i = k; i < s.length; i++) {
      const subStr = s.slice(k, i + 1)
      if (isPalindrome(subStr)) {
        path.push(subStr)
      } else {
        continue
      }
      backTracking(i + 1)
      path.pop()
    }
  }

  backTracking(0)

  return res
}
```
