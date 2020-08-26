### 题目描述

输入一棵二叉树，求该树的深度。从根结点到叶结点依次经过的结点（含根、叶结点）形成树的一条路径，最长路径的长度为树的深度。

### 思路一:递归

```
//解法1：递归
//时间复杂度：O(n)
//空间复杂度：O(n),在最好的情况下（树是完全平衡的）树的高度log(N)。空间复杂度将是O(log(N))
//思路：DFS,每个节点的最大深度=max(左子树最大深度，右子树最大深度)+1
```

### 代码一

```js
function TreeDepth(pRoot)
{
    if(!pRoot) return 0;
    let leftDepth = TreeDepth(pRoot.left);
    let rightDepth = TreeDepth(pRoot.right);
    return Math.max(leftDepth, rightDepth) + 1;
}
```

### 思路二：广度优先遍历BFS（特点："从左到右，从上到下"）-队列

```
1、通过创建FIFO队列，迭代每一层元素，每迭代一层，level+1；
2、通过实时维护队列的len，来保证当前层是否遍历结束，遍历完进入下一层，depth加1

```

### 代码二

```js
function TreeDepth(pRoot)
{
    if(!pRoot) return 0;
    let queue = [], depth = 0;
    queue.push(pRoot);
    while(queue.length){
        let len = queue.length;
        while(len){
            let node = queue.shift();
            if(node.left){
                queue.push(node.left);
            }
            if(node.right){
                queue.push(node.right);
            }
            len--;
        }
        depth++
    }
    return depth;
}
```

