![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给定一个有相同值的二叉搜索树（**BST**），找出 **BST** 中的所有众数（出现频率最高的元素）。

假定 BST 有如下定义：

- 结点左子树中所含结点的值小于等于当前结点的值
- 结点右子树中所含结点的值大于等于当前结点的值
- 左子树和右子树都是二叉搜索树

例如：

```javascript
给定 BST [1,null,2,2],

   1
    \
     2
    /
   2
返回[2].
```

提示：如果众数超过1个，不需考虑输出顺序

进阶：你可以不使用额外的空间吗？（假设由递归产生的隐式调用栈的开销不被计算在内）

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/find-mode-in-binary-search-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。




## 解题思路

由于 `BST`（二叉搜索树）的特殊性，我们采用递归来中序遍历，访问的节点值是有序的。然后重复节点，用计数器进行累加即可，如果有新值出现，则更新新值，然后计数器重置为 1。然后对于当前次数超过了最大值，则更新当前最大值，如果等于最大值，则代表出现了相同频率的数字，加入即可。

如果次数小于最大值，不需要什么操作。

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
var findMode = function(root) {
    let cnt = 0;
    let pre = 0;
    let res = [];
    let maxCnt = 0;
    let handle = (cur) => {
        // 相同的数，累加
        if(cur === pre){
            cnt++;
        }else{
            // 有新数出现，重新置计数器为1，更新新数
            pre = cur;
            cnt = 1;
        }
        // 如果次数超过了最大值，更新当前最大值
        if(cnt > maxCnt){
            maxCnt = cnt;
            res = [cur];
        // 如果有相同频率的数字出现，直接加入
        }else if(cnt === maxCnt){
            res.push(cur);
        }
    }
    // 二叉搜索树，递归中序遍历方式
    let inOrder = (root) =>{
        if(!root) return null;
        inOrder(root.left);
        handle(root.val);
        inOrder(root.right);
    }
    inOrder(root);
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


