# 监控二叉树

> 难度：困难
>
> 次数：1
>
> https://leetcode.cn/problems/binary-tree-cameras

## 题目

给定一个二叉树，我们在树的节点上安装摄像头。

节点上的每个摄影头都可以监视其父对象、自身及其直接子对象。

计算监控树的所有节点所需的最小摄像头数量。

### 示例

#### 示例 1：

![bst_cameras_01](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/29/bst_cameras_01.png)

```
输入：[0,0,null,0,0]
输出：1
解释：如图所示，一台摄像头足以监控所有节点。
```

#### 示例 2：

![bst_cameras_02](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/29/bst_cameras_02.png)

```
输入：[0,0,null,0,null,0,null,null,0]
输出：2
解释：需要至少两个摄像头来监视树的所有节点。 上图显示了摄像头放置的有效位置之一。
```

## 解法

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var minCameraCover = function (root) {
  const NOT_COVER = 0
  const HAVE_CAMERA = 1
  const COVER = 2

  let result = 0

  const traversal = cur => {
    if (cur === null) {
      return COVER
    }

    const left = traversal(cur.left)
    const right = traversal(cur.right)

    if (left === COVER && right === COVER) {
      return NOT_COVER
    }

    if (left === NOT_COVER || right === NOT_COVER) {
      result++
      return HAVE_CAMERA
    }

    if (left === HAVE_CAMERA || right === HAVE_CAMERA) {
      return COVER
    }
  }

  if (traversal(root) === 0) {
    result++
  }

  return result
}
```
