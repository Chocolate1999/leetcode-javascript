![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。

说明: 叶子节点是指没有子节点的节点。

示例:

```javascript
给定如下二叉树，以及目标和 sum = 22，

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
```

返回:

```javascript
[
   [5,4,11,2],
   [5,8,4,5]
]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/path-sum-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路
`dfs`，进行深度优先遍历，一直遍历到子节点为止，进行一次判断，如果当前 `sum`为 0 ，那么就是我们想要的结果，然后注意 `js` 语法中形参如果是数组，那么我们拿到的是引用值，可以拷贝一份。

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
 * @param {number} sum
 * @return {number[][]}
 */
var pathSum = function (root, sum) {
    if(!root) return [];
    let res = [];
    let dfs = (cur, root, sum) => {
        if (root == null) return 0;
        // 拷贝一份
        cur = [...cur,root.val];
        sum -= root.val;
        if (!root.left && !root.right && sum == 0) {
            res.push(cur);
            return;
        }
        // 优先遍历左子树
        root.left && dfs(cur, root.left, sum);
        root.right && dfs(cur, root.right, sum);
    }
    dfs([], root, sum);
    return res;
};
```

不太明白的小伙伴，这里给一个友好的提示，我们可以打印一下拷贝出来的`cur`，结合图示应该就好理解了，经典的 `dfs`实现的先序遍历。

```javascript
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
```

```javascript
[ 5 ]
[ 5, 4 ]
[ 5, 4, 11 ]
[ 5, 4, 11, 7 ]
[ 5, 4, 11, 2 ]
[ 5, 8 ]
[ 5, 8, 13 ]
[ 5, 8, 4 ]
[ 5, 8, 4, 5 ]
[ 5, 8, 4, 1 ]
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


