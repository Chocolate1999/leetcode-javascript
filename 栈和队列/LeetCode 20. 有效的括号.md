

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述


给定一个只包括` '('，')'，'{'，'}'，'['，']' `的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

示例 1:

```javascript
输入: "()"
输出: true
```

示例 2:

```javascript
输入: "()[]{}"
输出: true
```

示例 3:

```javascript
输入: "(]"
输出: false
```

示例 4:

```javascript
输入: "([)]"
输出: false
```

示例 5:

```javascript
输入: "{[]}"
输出: true
```


## 题解

发现越靠后的左括号，最先匹配，也就是`后进先出`的思想，于是考虑使用栈这个数据结构。

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
  // 如果是奇数，不可能匹配成功，直接返回false
  if(s.length & 1) return false
  let stack = []
  for(let i=0;i<s.length;i++){
    if(s[i] === '(' || s[i] === '{' || s[i] === '[') stack.push(s[i])
    else if(s[i] === ')' && stack[stack.length-1] === '(') stack.pop()
    else if(s[i] === '}' && stack[stack.length-1] === '{') stack.pop()
    else if(s[i] === ']' && stack[stack.length-1] === '[') stack.pop()
    else return false
  }
  return !stack.length
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