![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
在一个由 0 和 1 组成的二维矩阵内，找到只包含 1 的最大正方形，并返回其面积。

示例:

```javascript
输入: 

1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0

输出: 4
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/maximal-square
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


## 解题思路
要想求得最大正方形，通过找规律，我们不难发现，对于(i > 0 && j > 0)情况，当前位置边长长度等于左，左上，上三个方向边长长度的最小值，然后加1，于是我们遍历整个矩阵，对于当前值为1的情况，我们每次求一下它能拓展到的最大边长，然后每次迭代求出结果的最大边长，那么面积就是边长*边长返回即可。


```javascript
/**
 * @param {character[][]} matrix
 * @return {number}
 */
var maximalSquare = function (matrix) {
    if (!matrix || !matrix.length) return 0;
    let res = 0; // 设置最长边长变量
    let n = matrix.length, m = matrix[0].length;
    for (let i = 0; i < n; i++) {
        for (let j = 0; j < m; j++) {
            if (matrix[i][j] == 1) {
                // 对于(i > 0 && j > 0)情况，当前位置边长长度等于左，左上，上三个方向边长长度的最小值，然后加1
                (i > 0 && j > 0) && (matrix[i][j] = Math.min(matrix[i - 1][j], matrix[i - 1][j - 1], matrix[i][j - 1]) + 1);
            }
            res = Math.max(res, matrix[i][j]); // 迭代求最长边长
        }
    }
    return res ** 2; // 返回边长*边长
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


