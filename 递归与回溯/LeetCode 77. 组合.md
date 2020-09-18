![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

给定两个整数 n 和 k，返回 1 ... n 中所有可能的 k 个数的组合。

示例:

```javascript
输入: n = 4, k = 2
输出:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/combinations
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 解题思路
直接套用组合题解题模板即可

```javascript
var combine = function (n, k) {
  let res = [];
  let dfs = (t, start) => {
    if (t.length === k) {
      res.push(t);
      return;
    }
    for (let i = start; i <= n; i++) {
      t.push(i);
      dfs(t.slice(), i + 1);
      t.pop();
    }
  }
  dfs([], 1);
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



