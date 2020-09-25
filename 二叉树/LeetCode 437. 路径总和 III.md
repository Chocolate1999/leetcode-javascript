![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给定一个二叉树，它的每个结点都存放着一个整数值。

找出路径和等于给定数值的路径总数。

路径不需要从根节点开始，也不需要在叶子节点结束，但是路径方向必须是向下的（只能从父节点到子节点）。

二叉树不超过1000个节点，且节点数值范围是 [-1000000,1000000] 的整数。

示例：

```javascript
root = [10,5,-3,3,2,null,11,3,-2,null,1], sum = 8

      10
     /  \
    5   -3
   / \    \
  3   2   11
 / \   \
3  -2   1

返回 3。和等于 8 的路径有:

1.  5 -> 3
2.  5 -> 2 -> 1
3.  -3 -> 11
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/path-sum-iii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。




## 解题思路

本题采用方式就是先序遍历，对于遍历到的每个节点，我们都进行一次 `dfs`，但是考虑本题的数字范围为负数，对于当前一条路我们得到了一条路径后，假如后面还有路可以走，那么我们还是继续走，因为后面可能出现正负抵消的情况。

面试中如果遇到题例没有明确说明数字范围，建议和面试官沟通。

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
 * @param {number} sum
 * @return {number}
 */
var pathSum = function (root, sum) {
    // 定义一个计时器
    let cnt = 0;
    // 先序遍历所有根节点
    let preOrder = (root, sum) => {
        if (root == null) return;
        dfs(root, sum);
        preOrder(root.left, sum);
        preOrder(root.right, sum);
    }
    let dfs = (root, sum) => {
        if (root == null) return;
        sum -= root.val;
        // 求和满足，累加
        if (sum === 0) cnt++;
        // 递归左右子树，如果当前和为0了，但是下面还是有路，还是继续走下去
        // 因为本题数值范围存在负数，可能继续走下去还存在满足条件的路径
        dfs(root.left, sum);
        dfs(root.right, sum);
    }
    preOrder(root, sum);
    return cnt;
};
```


## 最后
文章产出不易，还望各位小伙伴们支持一波！

往期精选：

<a href="https://github.com/Chocolate1999/Front-end-learning-to-organize-notes">小狮子前端の笔记仓库</a>

<a href="https://github.com/Chocolate1999/leetcode-javascript">leetcode-javascript：LeetCode 力扣的 JavaScript 解题仓库，前端刷题路线（思维导图）</a>

小伙伴们可以在Issues中提交自己的解题代码，🤝 欢迎Contributing，可打卡刷题，Give a ⭐️ if this project helped you!


<a href="https://yangchaoyi.vip/">访问超逸の博客</a>，方便小伙伴阅读玩耍~

![](https://img-blog.csdnimg.cn/2020090211491121.png#pic_center)

```javascript
学如逆水行舟，不进则退
```


