![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
有重复字符串的排列组合。编写一种方法，计算某字符串的所有排列组合。

示例1:

```javascript
 输入：S = "qqe"
 输出：["eqq","qeq","qqe"]
```

示例2:

```javascript
 输入：S = "ab"
 输出：["ab", "ba"]
```

提示:

```javascript
字符都是英文字母。
字符串长度在[1, 9]之间。
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/permutation-ii-lcci
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路

全排列，直接用回溯法即可，数据量比较小，暴力完事~

```javascript
var permutation = function (S) {
  let res = new Set()
  let vis = []
  let dfs = (t) => {
    if (t.length === S.length) return res.add(t)
    for (let i = 0; i < S.length; i++) {
      if (vis[i]) continue
      vis[i] = true
      dfs(t + S[i])
      vis[i] = false
    }
  }
  dfs('')
  return [...res]
}
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


