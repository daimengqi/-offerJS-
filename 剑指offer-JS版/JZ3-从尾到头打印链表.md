### 题目描述
输入一个链表，按链表从尾到头的顺序返回一个ArrayList。

### 思路一

调用内置函数，先将链表每个结点的值存入数组中，然后通过数组的reverse方法，即可从尾到头打印

### 代码一

```js
/*function ListNode(x){
    this.val = x;
    this.next = null;
}*/
function printListFromTailToHead(head)
{
    var arr = [];
    while(head){
        arr.push(head.val);
        head = head.next;
    }
    return arr.reverse();
}
```

### 思路二

调用内置函数，先将链表每个结点的值依次从数组的头部开始存入，然后打印数组即可

### 代码二

```js
function printListFromTailToHead(head)
{
    var arr = [];
    while(head){
        arr.unshift(head.val);
        head = head.next;
    }
    return arr;
}

```

