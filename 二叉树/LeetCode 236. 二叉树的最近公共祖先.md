![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。

百度百科中最近公共祖先的定义为：“对于有根树 T 的两个结点 p、q，最近公共祖先表示为一个结点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（**一个节点也可以是它自己的祖先**）。”

例如，给定如下二叉树:  `root = [3,5,1,6,2,0,8,null,null,7,4]`

![=](https://img-blog.csdnimg.cn/20200924184344131.png#pic_center)


 

示例 1:

```javascript
输入: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
输出: 3
解释: 节点 5 和节点 1 的最近公共祖先是节点 3。
```

示例 2:

```javascript
输入: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
输出: 5
解释: 节点 5 和节点 4 的最近公共祖先是节点 5。因为根据定义最近公共祖先节点可以为节点本身。
```

说明:

```javascript
所有节点的值都是唯一的。
p、q 为不同节点且均存在于给定的二叉树中。
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路
根据定义，我们知道，假设 `root` 为 `p、q` 的最近公共祖先，则只可能有如下几种情况：

- p、q 在 root 的子树中，那么 p、q 分在 root 的左右子树中
- 如果 p = root，那么 q 会在 p 的左右子树中，直接返回 p 即可
- 如果 q = root，与上述类似

然后我们采用 `后序遍历`的方式，先遍历左右子树，看能不能找到对应 `p` 和 `q` 节点。

如果左右子树都能找到，那么代表p、q 分在 root 的左右子树中，直接返回 root 节点
如果左子树找到，右子树没找到，那么就返回左子树的查找结果
如果右子树找到，左子树没找到，那么就返回右子树的查找结果

![](https://img-blog.csdnimg.cn/20200924184419688.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)

参考 <a href="https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree/solution/236-er-cha-shu-de-zui-jin-gong-gong-zu-xian-hou-xu/">Krahets</a> 大佬图解


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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function (root, p, q) {
    if (!root || root == p || root == q) return root;
    let left = lowestCommonAncestor(root.left, p, q);
    let right = lowestCommonAncestor(root.right, p, q);
    // 如果当前root 在左右子树下可以找到 p q 那么这个root就是它们的最近公共祖先
    if(left && right) return root; 
    // 如果当前root 只有左子树有节点，那么这个节点本身就是p、q的祖先
    else if(left) return left;
    // 如果当前root 只有右子树有节点，那么这个节点本身就是p、q的祖先
    else if(right) return right;
    // 如果左右子树都找不到p、q，那么这颗树不存在这两个点，直接返回 null 即可
    //（但本题告知已存在，所以下面这一行代码可写可不写都能通过）
    return null;
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


