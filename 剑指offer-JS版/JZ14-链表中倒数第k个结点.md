### 题目描述
输入一个链表，输出该链表中倒数第k个结点。

### 思路一：快慢指针

//解法：双指针法。让快指针和慢指针之间存在k-1个距离。
//首先两个指针都在head处，快指针先向前移动k-1次，处于第k个节点处。
//然后快慢指针同时同速出发，当快指针到达终点，慢指针正好处于倒数第k个节点处。

### 代码一

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function FindKthToTail(head, k)
{
    if(!head || k == 0) return null;
    let fast = head, slow = head;
    while(k){
        if(fast == null) return null;
        fast = fast.next;
        k--;
    }
    while(fast){
        fast = fast.next;
        slow = slow.next;
    }
    return slow;
}
```

