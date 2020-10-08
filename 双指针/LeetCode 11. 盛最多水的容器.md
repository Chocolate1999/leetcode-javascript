![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
给你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

**说明**：你不能倾斜容器，且 n 的值至少为 2。

![](https://img-blog.csdnimg.cn/20201008101004524.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjQyOTcxOA==,size_16,color_FFFFFF,t_70#pic_center)
图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。

 

示例：

```javascript
输入：[1,8,6,2,5,4,8,3,7]
输出：49
```
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/container-with-most-water
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


## 解题思路

双指针做法，我们需要枚举所有情况，有一点贪心的思想，每次我们得看短的板子让我们容纳的面积。每次都选择左右指针最短的那个板子，计算出当前容纳的最多的水，然后从短的板子指针出发向内缩，这样不断求，最终我们可以枚举所有情况，自然可以枚举出最大容器面积。

```javascript
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function (height) {
    let len = height.length;
    let L = 0;
    let R = len - 1;
    let res = 0;
    while (L < R) {
        if (height[L] < height[R]) {  // 选择短板效应
            let ans = height[L] * (R - L);
            L++;
            res = Math.max(res, ans); // 求当前容纳最多的水
        } else {
            let ans = height[R] * (R - L);
            res = Math.max(res, ans);
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


