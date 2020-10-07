![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

注意:
不能使用代码库中的排序函数来解决这道题。

示例:

```javascript
输入: [2,0,2,1,1,0]
输出: [0,0,1,1,2,2]
```

进阶：

一个直观的解决方案是使用计数排序的两趟扫描算法。
首先，迭代计算出0、1 和 2 元素的个数，然后按照0、1、2的排序，重写当前数组。
你能想出一个仅使用常数空间的一趟扫描算法吗？

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/sort-colors
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 解题思路

双指针，当前值为2，那么就和右边指针进行交换，反之当前值为0，那么就和左边指针进行交换，为1就不动。

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function (nums) {
    let len = nums.length;
    let L = 0;
    let R = len - 1;
    let i = 0;
    while (i <= R) {
        while (nums[i] == 2 && i < R) { // 当前值为2，那么就和右边指针进行交换
            [nums[i], nums[R]] = [nums[R], nums[i]];
            R--;
        }
        while (nums[i] == 0 && i > L) { // 当前值为0，那么就和左边指针进行交换
            [nums[i], nums[L]] = [nums[L], nums[i]];
            L++;
        }
        i++;
    }
    return nums;
};
```

我想下面这份代码应该会更好理解一点：

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function (nums) {
    let len = nums.length;
    let L = 0;
    let R = len - 1;
    let i = 0;
    while (i <= R) {
        if (nums[i] == 0) { // 当前值为0，那么就和左边指针进行交换
            [nums[i], nums[L]] = [nums[L], nums[i]];
            L++;
            i++;
        } else if (nums[i] == 2) { // 当前值为2，那么就和右边指针进行交换
            [nums[i], nums[R]] = [nums[R], nums[i]];
            R--;
        } else {
            i++;
        }
    }
    return nums;
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


