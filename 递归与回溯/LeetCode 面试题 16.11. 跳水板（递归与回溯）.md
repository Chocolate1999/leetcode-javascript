![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
你正在使用一堆木板建造跳水板。有两种类型的木板，其中长度较短的木板长度为shorter，长度较长的木板长度为longer。你必须正好使用k块木板。编写一个方法，生成跳水板所有可能的长度。

返回的长度需要从小到大排列。

示例 1

```javascript
输入：
shorter = 1
longer = 2

k = 3
输出： [3,4,5,6]
解释：
可以使用 3 次 shorter，得到结果 3；使用 2 次 shorter 和 1 次 longer，得到结果 4 。以此类推，得到最终结果。
```
提示：

```javascript
0 < shorter <= longer
0 <= k <= 100000
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/diving-board-lcci
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路
排列组合也算比较简单，需要 `k` 个板子，当我们短板有 `i` 个的时候，长板子就是 `k-i` 个，由于题目要求是将结果从小到大进行排序，那么我们起初就尽可能多的取短板子，最后结果就是通过 `[0,k]` 范围内遍历一遍即可。

对于特殊情况，即短板和长板长度相同时，我们只需要返回 `k*len` 即可，不然会重复计算。

```javascript
var divingBoard = function(shorter, longer, k) {
    if(k===0) return []
    if(shorter === longer) return [k*shorter]
    let res = []
    for(let i=k;i>=0;i--){
        let shortCnt = i
        let longCnt = k-i
        let cnt = shortCnt*shorter + longCnt*longer
        res.push(cnt)
    }
    return res
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


