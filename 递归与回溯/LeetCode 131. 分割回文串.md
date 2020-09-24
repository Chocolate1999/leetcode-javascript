![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

给定一个字符串 `s`，将 `s` 分割成一些子串，使每个子串都是回文串。

返回 s 所有可能的分割方案。

示例:

```javascript
输入: "aab"
输出:
[
  ["aa","b"],
  ["a","a","b"]
]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/palindrome-partitioning
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


## 解题思路
借鉴 <a href="https://leetcode-cn.com/problems/palindrome-partitioning/solution/chui-su-fa-jian-dan-jie-ti-chao-qing-xi-tu-li-by-z/">zesong-wang-c</a> 大佬的图解
![](https://img-blog.csdnimg.cn/20200924142102395.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)
本题采用回溯思想，看上图基本已经明白，每次进行一次切割，直到切到最后一个元素，然后压入结果集合里，期间对于每次切割的字符串，我们判断一下是否是回文，如果不是，直接减掉即可。

和组合的思想有点类似。

```javascript
// 判断是否是回文
function isPal(str) {
  let len = Math.floor(str.length / 2);
  if (len === 0) {
    return true;
  }
  let add = str.length % 2 === 0 ? 0 : 1;
  let subStr = str.slice(0, len);
  for (let i = 0; i < len; i++) {
    if (subStr[len - i - 1] !== str[len + add + i]) {
      return false;
    }
  }
  return true;
}
var partition = function (s) {
  let res = [];
  let dfs = (cur, start) => {
    // 当前已经到达了最后一个元素
    if (start >= s.length) {
      res.push(cur.slice());
      return;
    }
    for (let i = start; i < s.length; i++) {
      // 字符串切割
      let str = s.slice(start, i + 1);
      if (str && isPal(str) ) {
        cur.push(str);
        dfs(cur, i + 1);
        // 回溯
        cur.pop();
      }
    }
  }
  dfs([], 0);
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


