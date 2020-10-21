![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
你的朋友正在使用键盘输入他的名字 `name`。偶尔，在键入字符 `c` 时，按键可能会被长按，而字符可能被输入 1 次或多次。

你将会检查键盘输入的字符 `typed`。如果它对应的可能是你的朋友的名字（其中一些字符可能被长按），那么就返回 `True`。

 

示例 1：

```javascript
输入：name = "alex", typed = "aaleex"
输出：true
解释：'alex' 中的 'a' 和 'e' 被长按。
```

示例 2：

```javascript
输入：name = "saeed", typed = "ssaaedd"
输出：false
解释：'e' 一定需要被键入两次，但在 typed 的输出中不是这样。
```

示例 3：

```javascript
输入：name = "leelee", typed = "lleeelee"
输出：true
```

示例 4：

```javascript
输入：name = "laiden", typed = "laiden"
输出：true
解释：长按名字中的字符并不是必要的。
```

 

提示：

- `name.length` <= 1000
- `typed.length` <= 1000
- `name` 和 `typed` 的字符都是小写字母。
 

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/long-pressed-name
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。




## 解题思路
显而易见，采用双指针做法，通过 `cnt` 计数统计字符匹配成功个数，然后通过双指针进行比较匹配，其中有几个地方注意一下：

- 如果 `typed` 和 `name` 的当前索引前一位都不相等的话，那么名字就不对应，直接跳出去，这里算是小小的优化了一下。
- 当 `typed` 走完才能跳出去，如果是 `i == n`  就跳出去的话，这种情况：name：abc | typed：abcd 就会判断出错


```javascript
/**
 * @param {string} name
 * @param {string} typed
 * @return {boolean}
 */
var isLongPressedName = function (name, typed) {
    let n = name.length; // 求出字符串长度
    let m = typed.length;
    let cnt = 0; // 统计匹配成功个数
    let i = 0, j = 0; // 双指针
    let flag = false; // 判断是否中途遇到不匹配阶段
    while (1) {
        if (name[i] == typed[j]) { // 匹配成功
            i++ , cnt++ , j++;
        } else {
            if (typed[j] == name[i - 1]) {
                j++;
            } else {
                // 如果 typed 和 name 当前索引前一位都不相等的话，那么名字就不对应，直接跳出去
                flag = true;
            }
        }
        if (flag) break;
        if (j == m) break; // 当 typed走完才能跳出去，如果是 i == n  就跳出去的话，这种情况：abc | abcd 就会判断出错
    }
    if (cnt === n && j === m) return true;
    else return false;
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


