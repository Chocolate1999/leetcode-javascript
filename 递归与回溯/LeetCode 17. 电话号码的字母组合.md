![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。

给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

![](https://img-blog.csdnimg.cn/20200924151801985.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)


示例:

```javascript
输入："23"
输出：["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

说明:

```javascript
尽管上面的答案是按字典序排列的，但是你可以任意选择答案输出的顺序。
```


## 解题思路

采用回溯做法，对于当前选项，我们可以重复选择，所以 `for` 循环那里从 0 开始，对于字母组合我们做一个 `map`映射即可。

![](https://img-blog.csdnimg.cn/2020092415195179.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)


参考 <a href="https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/solution/shou-hua-tu-jie-liang-chong-jie-fa-dfshui-su-bfsya/">xiao_ben_zhu</a> 大佬的图解

```javascript
var letterCombinations = function (digits) {
  if(!digits.length) return [];
  // 直接映射
  const map = { '2': 'abc', '3': 'def', '4': 'ghi', '5': 'jkl', '6': 'mno', '7': 'pqrs', '8': 'tuv', '9': 'wxyz' };
  let res = [];
  let dfs = (cur, start) => {
    if (start >= digits.length) {
      res.push(cur);
      return;
    }
    // 取当前可选的字母组合
    let str = map[digits[start]];
    for (let i = 0; i < str.length; i++) {
      dfs(cur + str[i], start + 1);
    }
  }
  dfs('', 0);
  return res;
};
```
解法2

这个是没用回溯之前写的一份代码，简单来说就是利用了**层次遍历**的特性，反正每次取字母都是可以重复的，直接遍历即可，然后进队列。

```javascript
var letterCombinations = function(digits) {
  if(!digits.length) return []
  const map = { '2': 'abc', '3': 'def', '4': 'ghi', '5': 'jkl', '6': 'mno', '7': 'pqrs', '8': 'tuv', '9': 'wxyz' };
  let queue = []
  queue.push('')
  for(let i=0;i<digits.length;i++){
      let size = queue.length
      while(size--){
          let cur = queue.shift()
          let str = map[digits[i]]
          for(let j=0;j<str.length;j++){
              queue.push(cur+str[j])
          }
      }
  }
  return queue
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



