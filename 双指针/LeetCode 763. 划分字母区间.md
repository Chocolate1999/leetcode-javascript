![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
字符串 `S` 由小写字母组成。我们要把这个字符串划分为尽可能多的片段，同一个字母只会出现在其中的一个片段。返回一个表示每个字符串片段的长度的列表。


示例 1：

```javascript
输入：S = "ababcbacadefegdehijhklij"
输出：[9,7,8]
解释：
划分结果为 "ababcbaca", "defegde", "hijhklij"。
每个字母最多出现在一个片段中。
像 "ababcbacadefegde", "hijhklij" 的划分是错误的，因为划分的片段数较少。
```

提示：

- `S` 的长度在 `[1, 500]` 之间。
- `S` 只包含小写字母 `'a'` 到 `'z'` 。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/partition-labels
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


## 解题思路
此题是一个挺有意思的题，既有**贪心**的味道，又有**双指针**的味道，下面说一下解题思路：

首先维护一个 `map`，它用来统计字当前字母的位置，而我们通过遍历就可以记录得到每个字母的最远位置。

然后，再次遍历字符串时，我们既可以得到当前字母的最远位置，根据贪心思想，为了让同一个字母只会出现在其中的一个片段，那么对于这个字母一定要是最远位置，我们就可以得到一个**范围区间**，即 `maxLen `。

得到了 `maxLen `后，我们还需要让 `i` 指针，即**尾指针**走到这个地方才算我们可以切分的片段。

（想想，如果不走到 `maxLen `的话，这个范围区间内的字母可能会有更远的位置，那么就无法满足让同一个字母只会出现在其中的一个片段这个条件了）

![](https://img-blog.csdnimg.cn/20201022104140397.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)

参考 <a href="https://leetcode-cn.com/problems/partition-labels/solution/shou-hua-tu-jie-hua-fen-zi-mu-qu-jian-ji-lu-zui-yu/">笨猪爆破组</a> 大佬图解。

```javascript
/**
 * @param {string} S
 * @return {number[]}
 */
var partitionLabels = function (S) {
    let map = {}; // 用来统计当前字母最远位置
    for (let i = 0; i < S.length; i++) {
        map[S[i]] = i; // 存储当前字母当前位置
    }
    let start = 0; // 头指针
    let res = [];
    let maxLen = 0;
    for (let i = 0; i < S.length; i++) {
        let curMaxLen = map[S[i]];
        maxLen = Math.max(maxLen, curMaxLen); // 计算出当前区间范围是否还可以继续扩大区间
        if (i === maxLen) {
            let tmp = i - start + 1;
            start = i + 1;
            res.push(tmp);  // 划分片段
        }
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


