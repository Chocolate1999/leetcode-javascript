![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给定一个二叉树，返回它的 前序 遍历。

 示例:

```javascript
输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [1,2,3]
```

进阶: 递归算法很简单，你可以通过迭代算法完成吗？

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/binary-tree-preorder-traversal
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。




## 解题思路

**递归解法**

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
 * @return {number[]}
 */
var preorderTraversal = function (root) {
    if (!root) return [];
    let res = [];
    let fun = (root) => {
        if (root) res.push(root.val);
        root.left && fun(root.left);
        root.right && fun(root.right);
    }
    fun(root);
    return res;
};
```

**迭代做法**

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
 * @return {number[]}
 */
var preorderTraversal = function (root) {
    if (!root) return [];
    let res = [];
    let queue = [root];
    while (queue.length) {
        let size = queue.length;
        while (size--) {
            // 取左孩子
            let node = queue.pop();
            res.push(node.val);
            // 优先放右孩子
            node.right && queue.push(node.right);
            node.left && queue.push(node.left);
        }
    }
    return res;
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


