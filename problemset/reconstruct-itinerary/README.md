# 重新安排行程

> 难度：困难
>
> 次数：1
>
> https://leetcode.cn/problems/reconstruct-itinerary

## 题目

给你一份航线列表 `tickets` ，其中 `tickets[i] = [fromi, toi]` 表示飞机出发和降落的机场地点。请你对该行程进行重新规划排序。

所有这些机票都属于一个从 `JFK`（肯尼迪国际机场）出发的先生，所以该行程必须从 `JFK` 开始。如果存在多种有效的行程，请你按字典排序返回最小的行程组合。

- 例如，行程 `["JFK", "LGA"]` 与 `["JFK", "LGB"]` 相比就更小，排序更靠前。

假定所有机票至少存在一种合理的行程。且所有的机票 **必须都用一次** 且 **只能用一次**。

### 示例

#### 示例 1：

![itinerary1-graph](https://assets.leetcode.com/uploads/2021/03/14/itinerary1-graph.jpg)

```
输入：tickets = [["MUC","LHR"],["JFK","MUC"],["SFO","SJC"],["LHR","SFO"]]
输出：["JFK","MUC","LHR","SFO","SJC"]
```

#### 示例 2：

![itinerary2-graph](https://assets.leetcode.com/uploads/2021/03/14/itinerary2-graph.jpg)

```
输入：tickets = [["JFK","SFO"],["JFK","ATL"],["SFO","ATL"],["ATL","JFK"],["ATL","SFO"]]
输出：["JFK","ATL","JFK","SFO","ATL","SFO"]
解释：另一种有效的行程是 ["JFK","SFO","ATL","JFK","ATL","SFO"] ，但是它字典排序更大更靠后。
```

## 解法

```javascript
/**
 * @param {string[][]} tickets
 * @return {string[]}
 */
var findItinerary = function (tickets) {
  let result = ['JFK']
  let map = {}

  for (const [from, to] of tickets) {
    if (!map[from]) {
      map[from] = []
    }
    map[from].push(to)
  }

  for (const from in map) {
    map[from].sort()
  }

  const backTracking = () => {
    if (result.length === tickets.length + 1) {
      return true
    }
    const toCityList = map[result[result.length - 1]]

    if (!toCityList || !toCityList.length) {
      return false
    }

    for (let i = 0; i < toCityList.length; i++) {
      const curCity = toCityList[i]
      result.push(curCity)
      toCityList.splice(i, 1)
      if (backTracking()) {
        return true
      }
      result.pop()
      toCityList.splice(i, 0, curCity)
    }
  }

  backTracking()

  return result
}
```
