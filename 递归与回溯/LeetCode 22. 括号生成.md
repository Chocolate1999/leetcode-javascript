![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
数字 n 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 有效的 括号组合。

 

示例：

```javascript
输入：n = 3
输出：[
       "((()))",
       "(()())",
       "(())()",
       "()(())",
       "()()()"
     ]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/generate-parentheses
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。




## 解题思路

这道题，看了大佬的题解，发现真是有意思，现在来解释一下。

我们可以直接走可行的情况，对于不可行的情况，自然就剪掉了。

关键在于左右括号如何选择，首先，对于左括号，起初我们必然是要选的，然后我们也可以全部选完，因此，只要有左括号我们必须选，而对于右括号而言，它的剩余数量必须大于剩余左括号数量，我们才能选右括号。

举个反例，假如我们现在已经有了 `(())`，`n = 3`，然后左右括号都还剩一个，如果理解选 `)`，岂不是就 `(()))`了，显示不是有效的括号，应该被剪掉才是，因此，我们必须严格右括号剩余数量必须大于剩余左括号数量，我们才能选右括号。
![](https://img-blog.csdnimg.cn/20200924154433537.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)
参考 <a href="https://leetcode-cn.com/problems/generate-parentheses/solution/shou-hua-tu-jie-gua-hao-sheng-cheng-hui-su-suan-fa/">笨猪爆破组</a> 大佬图解

```javascript
var generateParenthesis = function (n) {
  let res = [];
  let dfs = (cur, left, right) => {
    if (cur.length === 2 * n) {
      res.push(cur);
      return;
    }
    // 左括号还存在，就可以选左括号
    if (left > 0) dfs(cur + '(', left - 1, right);
    // 右括号数量要大于左括号，才可以选右括号
    if (right > left) dfs(cur + ')', left, right - 1);
  }
  dfs('', n, n);
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


