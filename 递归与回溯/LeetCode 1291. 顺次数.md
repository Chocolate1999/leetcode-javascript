![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

我们定义「顺次数」为：每一位上的数字都比前一位上的数字大 1 的整数。

请你返回由 [low, high] 范围内所有顺次数组成的 有序 列表（从小到大排序）。

 

示例 1：

```css
输出：low = 100, high = 300
输出：[123,234]
```

示例 2：

```css
输出：low = 1000, high = 13000
输出：[1234,2345,3456,4567,5678,6789,12345]
 
```

提示：

```css
10 <= low <= high <= 10^9
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/sequential-digits
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



## 解题思路
「顺次数」为：每一位上的数字都比前一位上的数字大 1 的整数。

也就是例如 `1234`这样的数字，然后给你一段区间确定范围。

官方给了枚举方式，反正数据量也不是很大，但是我觉得还是有很多数字没必要枚举，可以直接剪枝掉。我的做法是先求出最小值和最大值对应字符串的长度，即求出我们能枚举的数字的长度范围。

然后我们的起点的最小值从 `1` 开始，起点的最大值从 `10-len` 开始。为什么是 `10-len`？举例说明，示例1给的是 `[100,300]`范围的值，那么可枚举的长度 `len` 为 3，起点的最大值就位 10 - 3 = 7。那么此时顺次数为 `789` 但是不在我们区间范围内，舍弃。然后`8、9`开头的数字就不需要枚举了。 这样，我们就能剪掉一部门数据了。（虽然暴力是永远滴神...）

```css
/**
 * @param {number} low
 * @param {number} high
 * @return {number[]}
 */
var sequentialDigits = function(low, high) {
    let res = []
    let lowLen = low.toString().length
    let highLen = high.toString().length
    for(let i=lowLen;i<=highLen;i++){
        for(let j=1;j<=10-i;j++){
            let str = ''
            let num = j
            str += num
            let k = i-1
            while(k--){
                num++
                str += num
            }
            let ans = parseInt(str)
            if(ans>=low && ans<=high){
                res.push(ans)
            }
        }
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


