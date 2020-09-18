![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
找出所有相加之和为 `n` 的 `k` 个数的组合。组合中只允许含有 `1 - 9` 的正整数，并且每种组合中不存在重复的数字。

说明：

所有数字都是正整数。
解集不能包含重复的组合。 
示例 1:

```javascript
输入: k = 3, n = 7
输出: [[1,2,4]]
```

示例 2:

```javascript
输入: k = 3, n = 9
输出: [[1,2,6], [1,3,5], [2,3,4]]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/combination-sum-iii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。




## 解题思路
首先，还是搬运一下大佬的图解，然后我再来解释一番。
![](https://img-blog.csdnimg.cn/20200918154008515.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)
<a href="https://leetcode-cn.com/problems/combination-sum-iii/solution/shou-hua-tu-jie-216-zu-he-zong-he-iii-by-xiao_ben_/">参考xiao_ben_zhu大佬图解</a>

本题需要一层一层来，第一层我们可以有 `i`(1-9)个选择，而第二层的每一个值只有 `i+1`个选择了，因为不能重复。比如你第一次拿了 `2`，在下一次，你只能从 `3`开始拿了，如果还是 `1`的话就会有重复的组合了。这样我们也不用维护 `vis`数组来去重，因为每一层取的值是不一样的。

```javascript
var combinationSum3 = function (k, n) {
  let res = [];
  let dfs = (t, start, sum) => {
    if (t.length === k && sum === n) {
      res.push(t);
    }
    for (let i = start; i < 10; i++) {
      t.push(i);
      dfs(t.slice(), i + 1, sum + i);
      t.pop();
    }
  }
  dfs([], 1, 0);
  return res;
};
```



## 最后
文章产出不易，还望各位小伙伴们支持一波！

往期精选：

<a href="https://github.com/Chocolate1999/Front-end-learning-to-organize-notes">小狮子前端の笔记仓库</a>

<a href="https://yangchaoyi.vip/">访问超逸の博客</a>，方便小伙伴阅读玩耍~

![](https://img-blog.csdnimg.cn/2020090211491121.png#pic_center)

```javascript
学如逆水行舟，不进则退
```


