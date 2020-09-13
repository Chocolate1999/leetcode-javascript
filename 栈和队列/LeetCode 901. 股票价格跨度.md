![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
编写一个 `StockSpanner` 类，它收集某些股票的每日报价，并返回该股票当日价格的跨度。

今天股票价格的跨度被定义为股票价格小于或等于今天价格的最大连续日数（从今天开始往回数，包括今天）。

例如，如果未来7天股票的价格是` [100, 80, 60, 70, 60, 75, 85]`，那么股票跨度将是` [1, 1, 1, 2, 1, 4, 6]`。

 

示例：

```javascript
输入：["StockSpanner","next","next","next","next","next","next","next"], [[],[100],[80],[60],[70],[60],[75],[85]]
输出：[null,1,1,1,2,1,4,6]
解释：
首先，初始化 S = StockSpanner()，然后：
S.next(100) 被调用并返回 1，
S.next(80) 被调用并返回 1，
S.next(60) 被调用并返回 1，
S.next(70) 被调用并返回 2，
S.next(60) 被调用并返回 1，
S.next(75) 被调用并返回 4，
S.next(85) 被调用并返回 6。
```

```javascript
注意 (例如) S.next(75) 返回 4，因为截至今天的最后 4 个价格
(包括今天的价格 75) 小于或等于今天的价格。
```

提示：

```javascript
调用 StockSpanner.next(int price) 时，将有 1 <= price <= 10^5。
每个测试用例最多可以调用  10000 次 StockSpanner.next。
在所有测试用例中，最多调用 150000 次 StockSpanner.next。
此问题的总时间限制减少了 50%。
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/online-stock-span
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## 解题思路
正如题意，我们要求当前元素之前，比自己小（可以相等）的元素个数，并且元素个数包括本身，那么我们最后的结果应该还要加1.

于是按题意，我们采用跨度法，举个例子，对于例子6，1，2，3，4，9，从后往前逆推一下，当我们新插入9的时候，如果发现前一位的4比9小，那么是否说明比9小的数量就等于比4小的数量加1？然而这是错的，因为首位的6比9小，却比4大，因此截止数字的4时候，比4小的数量中并不包含6与9的对比。

因此，我们还要跳到 6 的位置再去计算小于等于自己的元素。

```javascript
var StockSpanner = function() {
    // 存储股票跨度
    this.spanner = []
    // 存储股票价格
    this.stockPrice = []
};

/** 
 * @param {number} price
 * @return {number}
 */
StockSpanner.prototype.next = function(price) {
    // 对于第一天进行特殊判断
    if(!this.spanner.length){
        this.spanner.push(1)
        this.stockPrice.push(price)
        // 直接返回1
        return 1
    }
    let cnt = 0
    let idx = this.stockPrice.length-1
    while(price >= this.stockPrice[idx] && idx>=0){
        cnt += this.spanner[idx]
        idx -= this.spanner[idx]
    }
    // 加上本身
    cnt++
    // 进行更新操作，将当前股票价格和跨度入栈
    this.spanner.push(cnt)
    this.stockPrice.push(price)
    return cnt
};

/**
 * Your StockSpanner object will be instantiated and called as such:
 * var obj = new StockSpanner()
 * var param_1 = obj.next(price)
 */
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

