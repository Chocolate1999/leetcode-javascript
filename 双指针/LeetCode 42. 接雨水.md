![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

给定 n 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。
![](https://img-blog.csdnimg.cn/20201008103143415.png#pic_center)

上面是由数组 `[0,1,0,2,1,0,1,3,2,1,2,1] `表示的高度图，在这种情况下，可以接 6 个单位的雨水（蓝色部分表示雨水）。 感谢 Marcos 贡献此图。

示例:

```javascript
输入: [0,1,0,2,1,0,1,3,2,1,2,1]
输出: 6
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/trapping-rain-water
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 解题思路

这个存放水，我们就需要看左边两边指针的柱子看谁的高度小了，当前是看高度小的了。

以左边为例：当前柱子存水量 = 最近最高柱子高度（只看左边到当前柱子） - 当前柱子高度

右边同理。

```javascript
/**
 * @param {number[]} height
 * @return {number}
 */
var trap = function (height) {
    let len = height.length;
    let L = 0, R = len - 1;
    let leftHeight = 0, rightHeight = 0;
    let res = 0;
    while (L < R) {
        if (height[L] < height[R]) { // 左边高度小，当然看左边
            leftHeight = Math.max(leftHeight, height[L]);
            res += leftHeight - height[L]; // 当前柱子能存放的水
            L++;
        } else { // 右边高度小，看右边
            rightHeight = Math.max(rightHeight, height[R]);
            res += rightHeight - height[R]; // 当前柱子能存放的水
            R--;
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


