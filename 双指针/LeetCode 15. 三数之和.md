![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

给你一个包含 n 个整数的数组 `nums`，判断 `nums` 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？请你找出所有满足条件且不重复的三元组。

注意：答案中不可以包含重复的三元组。


示例：

```javascript
给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/3sum
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路
因为不能有重复的解，为了简化操作，我们先对数组排序，于是判断一个元素是否重复，只需看它和它前面的元素是否相等即可


双指针的移动时，避免出现重复解

得到一个解后，需要左右指针向 “内” 收缩，为了避免指向重复的元素
- 左指针要在 left < right 的前提下，一直右移，直到指向不重复的元素
- 右指针要在 left < right 的前提下，一直左移，直到指向不重复的元素

优化点，如果当前元素值大于0了，由于我们事先排好序了，不存在三个数相加为0了，此时直接break就好了。




```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function (nums) {
    let len = nums.length;
    if (len < 2) return [];
    let res = [];
    nums.sort((a, b) => a - b); // 从小到大进行排序
    for (let i = 0; i < len - 2; i++) {
        if (nums[i] > 0) break;
        if (i > 0 && nums[i] === nums[i - 1]) continue; // 去掉重复项
        let L = i + 1;
        let R = len - 1;
        while (L < R) {
            let sum = nums[i] + nums[L] + nums[R]; // 三数之和
            if (sum === 0) {
                res.push([nums[i], nums[L], nums[R]]);
                while (L < R && nums[L] == nums[L + 1]) L++; // 去重，直到指向不一样的数
                while (L < R && nums[R] == nums[R - 1]) R--;
                L++;
                R--;
            } else if (sum < 0) {
                L++; // 和小于0，就是左边值太小了，往右移
            } else if (sum > 0) {
                R--; // 和大于0，就是右边值太大了，往左移
            }
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


