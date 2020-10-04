![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述
删除链表中等于给定值 val 的所有节点。

示例:

```javascript
输入: 1->2->6->3->4->5->6, val = 6
输出: 1->2->3->4->5
```

## 解题思路
创建一个新链表，遇到相同值的情况，将当前节点的next指向下一个节点的next，否则继续遍历。

```javascript
var removeElements = function(head, val) {
    let dummyHead = new ListNode(); // 哑结点
    dummyHead.next = head;
    let p = dummyHead;
    while(p.next){
        if(p.next.val === val){
            p.next = p.next.next;
        }else{
            p = p.next;
        }
    }
    return dummyHead.next;
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


