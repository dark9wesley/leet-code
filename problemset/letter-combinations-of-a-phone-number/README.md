# 两数之和

> 难度：中等
>
> 次数：1
>
> https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number

## 题目

给定一个仅包含数字 `2-9` 的字符串，返回所有它能表示的字母组合。答案可以按 **任意顺序** 返回。

给出数字到字母的映射如下（与电话按键相同）。注意 `1` 不对应任何字母。

![telephone](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2021/11/09/200px-telephone-keypad2svg.png)

### 示例

#### 示例 1：

```
输入：digits = "23"
输出：["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

#### 示例 2：

```
输入：digits = ""
输出：[]
```

#### 示例 3：

```
输入：digits = "2"
输出：["a","b","c"]
```

## 解法

```javascript
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function (digits) {
  const k = digits.length

  const map = ['', '', 'abc', 'def', 'ghi', 'jkl', 'mno', 'pqrs', 'tuv', 'wxyz']

  if (!k) return []
  if (k === 1) return map[digits].split('')

  const res = [],
    path = []

  const backTracking = index => {
    if (path.length === k) {
      res.push(path.join(''))
      return
    }

    for (const v of map[digits[index]]) {
      path.push(v)
      backTracking(index + 1)
      path.pop()
    }
  }

  backTracking(0)

  return res
}
```
