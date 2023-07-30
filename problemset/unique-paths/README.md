# 不同路径

> 难度：中等
>
> 次数：1
>
> https://leetcode.cn/problems/unique-paths

## 题目

一个机器人位于一个 `m x n` 网格的左上角 （起始点在下图中标记为 “Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish” ）。

问总共有多少条不同的路径？

### 示例

#### 示例 1：

![robot_maze](https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png)

```
输入：m = 3, n = 7
输出：28
```

#### 示例 2：

```
输入：m = 3, n = 2
输出：3
解释：
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -> 向下 -> 向下
2. 向下 -> 向下 -> 向右
3. 向下 -> 向右 -> 向下
```

#### 示例 4：

```
输入：m = 7, n = 3
输出：28
```

#### 示例 4：

```
输入：m = 3, n = 3
输出：6
```

## 解法

```javascript
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var uniquePaths = function (m, n) {
  const paths = new Array(m).fill().map(item => Array(n))

  for (let i = 0; i < m; i++) {
    paths[i][0] = 1
  }

  for (let i = 0; i < n; i++) {
    paths[0][i] = 1
  }

  for (let i = 1; i < m; i++) {
    for (let j = 1; j < n; j++) {
      paths[i][j] = paths[i - 1][j] + paths[i][j - 1]
    }
  }

  return paths[m - 1][n - 1]
}
```
