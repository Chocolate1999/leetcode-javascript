![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给定一个无重复元素的数组 `candidates` 和一个目标数 `target` ，找出 `candidates` 中所有可以使数字和为 `target` 的组合。

`candidates` 中的数字可以无限制重复被选取。

说明：

```javascript
所有数字（包括 target）都是正整数。
解集不能包含重复的组合。 
```

示例 1：

```javascript
输入：candidates = [2,3,6,7], target = 7,
所求解集为：
[
  [7],
  [2,2,3]
]
```

示例 2：

```javascript
输入：candidates = [2,3,5], target = 8,
所求解集为：
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]
```

 

提示：

```javascript
1 <= candidates.length <= 30
1 <= candidates[i] <= 200
candidate 中的每个元素都是独一无二的。
1 <= target <= 500
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/combination-sum
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 解题思路
这道题是组合题，但是这道题有意思的是当前元素可以重复无限制选取，那么我们可以改一下另外一道组合题的思路，下一层也从 `i`开始即可，然后本题元素重复，那么我们不需要进行排序然后剪枝了。

```javascript
// 当前元素可以无限制选取，下一层也从i开始取
dfs(t.slice(),i,sum+candidates[i]); 
```

![](https://img-blog.csdnimg.cn/20200918165742837.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)
<a href="https://leetcode-cn.com/problems/combination-sum/solution/shou-hua-tu-jie-zu-he-zong-he-combination-sum-by-x/">参考xiao_ben_zhu图解</a>

```javascript
var combinationSum = function(candidates, target) {
  let res = [];
  let dfs = (t,start,sum) => {
    if(sum >= target){ // 防止爆掉
      if(sum === target){
        res.push(t);
      }
      return;
    }
    for(let i=start;i<candidates.length;i++){
      t.push(candidates[i]);
      // 当前元素可以无限制选取，下一层也从i开始取
      dfs(t.slice(),i,sum+candidates[i]); 
      t.pop();
    }
  }
  dfs([],0,0);
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


