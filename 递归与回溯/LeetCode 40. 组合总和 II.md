![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

给定一个数组 `candidates `和一个目标数 target ，找出` candidates` 中所有可以使数字和为` target `的组合。

`candidates `中的每个数字在每个组合中只能使用一次。

说明：

所有数字（包括目标数）都是正整数。
解集不能包含重复的组合。 
示例 1:

```javascript
输入: candidates = [10,1,2,7,6,1,5], target = 8,
所求解集为:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
```

示例 2:

```javascript
输入: candidates = [2,5,2,1,2], target = 5,
所求解集为:
[
  [1,2,2],
  [5]
]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/combination-sum-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路

这道题也是一道组合题，但是这道题数组里面是存在重复元素的，组合题的话，为了更好地去重，我们可以先对数组进行排序，然后对于每一层如果相邻元素相同，就剪掉该分支即可。
![](https://img-blog.csdnimg.cn/20200918163049991.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)
<a href="https://leetcode-cn.com/problems/combination-sum-ii/solution/man-tan-wo-li-jie-de-hui-su-chang-wen-shou-hua-tu-/">参考xiao_ben_zhu大佬图解</a>

注意求和那里，如果只判断是否相等的话，可能会出现爆掉情况。


```javascript
var combinationSum2 = function (candidates, target) {
  let res = [];
  candidates.sort((a, b) => a - b);
  let dfs = (t, start, sum) => {
    if (sum >= target) { // 加这外层，超出范围了也终止，防爆栈
      if (sum === target) {
        res.push(t);
      }
      return;
    }
    // 组合
    for (let i = start; i < candidates.length; i++) {
      // 组合元素不能重复，去掉同一层重复的元素
      if (i > start && candidates[i] == candidates[i - 1]) continue;
      t.push(candidates[i]);
      // 组合元素去重，即当前选择和下一层的不能重复
      dfs(t.slice(), i + 1, sum + candidates[i]);
      t.pop();
    }
  }
  dfs([], 0, 0);
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


