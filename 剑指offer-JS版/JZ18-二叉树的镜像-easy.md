### 题目描述

![image-20200725215030903](C:\Users\DMQ\AppData\Roaming\Typora\typora-user-images\image-20200725215030903.png)

### 思路一：递归



### 代码一

```js
function Mirror(root)
{
    if(!root) return ;
    [root.left, root.right] = [root.right, root.left];
    Mirror(root.left);
    Mirror(root.right);
}
```

### 思路二：BFS迭代

```
BFS广度优先遍历，在将左右子树加入到栈之前，先把左右子数调换位置
```

### 代码二

```js
function Mirror(root)
{
    if(!root) return ;
    let stack = [];
    stack.push(root);
    while(stack.length){
        let node = stack.pop();
        [node.left, node.right] = [node.right, node.left]
        node.left && stack.push(node.left);
        node.right && stack.push(node.right);
    }
}
```

