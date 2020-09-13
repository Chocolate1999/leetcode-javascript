![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给定一个由` '('` 和` ')'` 括号组成的字符串 `S`，我们需要添加最少的括号`（ '(' 或是 ')'`，可以在任何位置），以使得到的括号字符串有效。

从形式上讲，只有满足下面几点之一，括号字符串才是有效的：

它是一个空字符串，或者
它可以被写成 `AB` （A 与 B 连接）, 其中 A 和 B 都是有效字符串，或者
它可以被写作 `(A)`，其中 A 是有效字符串。
给定一个括号字符串，返回为使结果字符串有效而必须添加的最少括号数。

 

示例 1：

```javascript
输入："())"
输出：1
```

示例 2：

```javascript
输入："((("
输出：3
```

示例 3：

```javascript
输入："()"
输出：0
```

示例 4：

```javascript
输入："()))(("
输出：4
```

提示：

```javascript
S.length <= 1000
S 只包含 '(' 和 ')' 字符。
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/minimum-add-to-make-parentheses-valid
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


## 解题思路
借助一个新栈，然后遍历当前字符串，如果当前栈顶元素和目前字符括号匹配，则弹出栈顶元素，否则进行入栈操作，最后需要的括号数即为栈剩余的元素个数

```javascript
/**
 * @param {string} S
 * @return {number}
 */
var minAddToMakeValid = function(S) {
    // 长度为0，无须添加
    if(!S.length) return 0
    let stack = []
    for(let i=0;i<S.length;i++){
        let ch = S[i]
        // 如果当前栈顶元素和目前字符括号匹配，则弹出栈顶元素
        if(ch === ')' && stack[stack.length-1] === '(') stack.pop()
        else stack.push(ch)
    }
    // 栈的剩余元素个数，即需要的括号数
    return stack.length
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