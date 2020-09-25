![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给你一个二叉树，请你返回其按 **层序遍历** 得到的节点值。 （即逐层地，从左到右访问所有节点）。

 

示例：

```javascript
二叉树：[3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
```

返回其层次遍历结果：

```javascript
[
  [3],
  [9,20],
  [15,7]
]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/binary-tree-level-order-traversal
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


## 解题思路
直接用 `BFS`，对于每一层初始化空数组，然后存放每一层的节点值，然后迭代即可。

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
 * @return {number[][]}
 */
var levelOrder = function (root) {
    if(!root) return [];
    let res = [];
    let queue = [root];
    let cnt = 0;
    while (queue.length) {
        let size = queue.length;
        // 每一层初始化一个空数组
        res.push([]);
        while (size--) {
            let node = queue.shift();
            // 每一层的节点都存着
            res[cnt].push(node.val);
            node.left && queue.push(node.left);
            node.right && queue.push(node.right);
        }
        // 迭代层次
        ++cnt;
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


