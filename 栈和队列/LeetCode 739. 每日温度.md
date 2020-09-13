![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
请根据每日 气温 列表，重新生成一个列表。对应位置的输出为：要想观测到更高的气温，至少需要等待的天数。如果气温在这之后都不会升高，请在该位置用 0 来代替。

例如，给定一个列表 `temperatures = [73, 74, 75, 71, 69, 72, 76, 73]`，你的输出应该是 `[1, 1, 4, 2, 1, 1, 0, 0]`。

提示：气温 列表长度的范围是 `[1, 30000]`。每个气温的值的均为华氏度，都是在 `[30, 100]` 范围内的整数。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/daily-temperatures
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路
本题用到了单调栈的思路，将原本需要  O(n^2) 的时间复杂度降低到了 O(n)。

我们只需要维护一个新栈，首先遍历整个数组，只要栈不为空，如果当前的数字大于栈顶元素，则必定是第一个大于它的元素，我们只需要求出相差距离，然后存入结果就好了。

维护的新栈存放的是我们的元素下标，这样我们求距离时就很方便了，本题我觉得可以说是单调栈的一个模板题。专栏后续会有单调栈其它题目，可以查阅哈。

```javascript
/**
 * @param {number[]} T
 * @return {number[]}
 */
var dailyTemperatures = function(T) {
    let stack = []
    // 初始化气温列表，默认值为0
    let res = new Array(T.length).fill(0)
    for(let i=0;i<T.length;i++){
        //将栈顶元素下标对应的值和当前元素进行比较
        while(T[i] > T[stack[stack.length-1]] && stack.length){
            let idx = stack.pop()
            res[idx] = i-idx
        }
        stack.push(i)
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

