![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9jZG4uanNkZWxpdnIubmV0L2doL2Nob2NvbGF0ZTE5OTkvY2RuL2ltZy8yMDIwMDgyODE0NTUyMS5qcGc?x-oss-process=image/format,png)
>仰望星空的人，不应该被嘲笑

## 题目描述

反转从位置 m 到 n 的链表。请使用一趟扫描完成反转。

说明:
1 ≤ m ≤ n ≤ 链表长度。

示例:

```javascript
输入: 1->2->3->4->5->NULL, m = 2, n = 4
输出: 1->4->3->2->5->NULL
```

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/reverse-linked-list-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


## 解题思路

**借助递归**

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} m
 * @param {number} n
 * @return {ListNode}
 */
var reverseBetween = function (head, m, n) {
    let reverse = (pre, cur) => {
        if (!cur) return pre;
        let tmp = cur.next;
        cur.next = pre;
        return reverse(cur, tmp);
    }
    let dummyHead = new ListNode();
    dummyHead.next = head;
    let p = dummyHead;
    let k = m - 1;
    // 先找到需要反转链表部分的前驱节点
    while (k--) {
        p = p.next;
    }
    // 保存前驱节点
    let front = p;
    // 找到需要反转链表部分的头节点
    let frontNode = front.next;
    k = n - m + 1;
    // 再找到需要反转链表部分的尾节点
    while (k--) {
        p = p.next;
    }
    // 找到需要反转链表部分的尾节点
    let endNode = p;
    // 保存后继节点
    let end = endNode.next;
    // 将后继值为空，开始反转链表
    endNode.next = null;
    front.next = reverse(null, frontNode);
    // 原本的反转链表部分的头节点现在变成了尾节点，指向原本的后继节点
    frontNode.next = end;
    return dummyHead.next;
};
```

**迭代解法**

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} m
 * @param {number} n
 * @return {ListNode}
 */
var reverseBetween = function(head, m, n) {
    let dummyHead = new ListNode();
    dummyHead.next = head;
    let p = dummyHead;
    let k = m-1;
    // 先找到需要反转链表部分的前驱节点
    while (k--) {
        p = p.next;
    }
    // 保存前驱节点
    let front = p;
    let pre = frontNode = front.next;
    let cur = pre.next;
    k = n-m;
    // 长度为3的链表需要反转2次，那么长度为n的链表需要反转n-1次
    while(k--){
        let tmp = cur.next;
        cur.next = pre;
        pre = cur;
        cur = tmp;
    }
    // 将原本前驱节点的next指向当前反转后的链表
    front.next = pre;
    // 原本反转链表的头节点现在变成了尾结点，指向后继节点
    frontNode.next = cur;
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



