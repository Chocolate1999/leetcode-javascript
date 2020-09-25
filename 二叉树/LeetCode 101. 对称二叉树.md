![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

给定一个二叉树，检查它是否是镜像对称的。

 

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

```javascript
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

 

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

```javascript
    1
   / \
  2   2
   \   \
   3    3
 
```

进阶：

你可以运用递归和迭代两种方法解决这个问题吗？

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/symmetric-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 解题思路
`dfs`，逐层进行比较，即自顶向底找，注意判断几个条件：

- 如果左右节点都为空，可以
- 如果左右节点一个为空，不可以
- 如果左右节点值不相等，不可以
- 最后递归左右子树镜像

![](https://img-blog.csdnimg.cn/img_convert/d53e8aef39ed61b5562b178e2b8c8606.png)
参考 <a href="https://leetcode-cn.com/problems/symmetric-tree/solution/dong-hua-yan-shi-101-dui-cheng-er-cha-shu-by-user7/">王尼玛</a> 大佬图解

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function (root) {
    if (!root) return true;
    let dfs = (left, right) => {
        // 如果左右节点都为空，可以
        if (left == null && right == null) return true;
        // 如果左右节点一个为空，不可以
        if(left == null || right == null) return false;
        // 如果左右节点值不相等，不可以
        if (left.val !== right.val) return false;
        // 递归左右子树镜像
        return dfs(left.left, right.right) && dfs(left.right, right.left);
    }
    return dfs(root.left, root.right);
};
```
**解法二**

通过队列逐步一层一层来比较，只要出现不对称的情况，直接返回 `false`。

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function (root) {
    if (!root) return true
    let queue = [root.left, root.right]
    while (queue.length) {
        let node1 = queue.shift()
        let node2 = queue.shift()
        if (!node1 && !node2) continue
        if (!node1 || !node2 || node1.val !== node2.val) return false
        queue.push(node1.left)
        queue.push(node2.right)
        queue.push(node1.right)
        queue.push(node2.left)
    }
    return true
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


