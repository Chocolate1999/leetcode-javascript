![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

给定一个 没有重复 数字的序列，返回其所有可能的全排列。

示例:

```javascript
输入: [1,2,3]
输出:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/permutations
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 解题思路
序列不重复就很简单了，维护一个 `vis`数组，不重复取就好了。

```javascript
var permute = function (nums) {
  let res = [];
  let vis = {};
  let dfs = (t) => {
    if (t.length == nums.length) {
      res.push(t);
    }
    for (let i = 0; i < nums.length; i++) {
      if (vis[i]) continue;
      vis[i] = true;
      t.push(nums[i]);
      dfs(t.slice());
      t.pop();
      vis[i] = false;
    }
  }
  dfs([]);
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


