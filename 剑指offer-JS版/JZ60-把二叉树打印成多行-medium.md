### 题目描述

从上到下按层打印二叉树，同一层结点从左至右输出。每一层输出一行。

### 思路一:bfs队列辅助遍历，toBePrinted和nextLevel变量辅助计算

### 代码一

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function Print(pRoot)
{
    if(!pRoot) return [];
    let queue = [];//BFS遍历的辅助队列,存放节点
    let res = [];//结果集合
    let path = [];//存储每一行的节点值
    let nextLevel = 0;//下一层节点数
    let toBePrinted = 1;//待打印节点数，根节点开始,所以当前层默认为待打印节点数为1
    queue.push(pRoot);
    while(queue.length){
        let node = queue.shift();
        path.push(node.val);
        if(node.left){
            queue.push(node.left);
            nextLevel++;//有左子树，因而下一层节点数+1
        }
        if(node.right){
            queue.push(node.right);
            nextLevel++;//有右子树，因而下一层节点数+1
        }
        toBePrinted--;//当前层的节点已存入，可以被打印
        if(toBePrinted === 0){
            res.push(path);//当前层所有节点存入结果集
            path = [];//清空存储节点值得数组
            toBePrinted = nextLevel;//更新下一层待打印节点数为下一层有的节点数
            nextLevel = 0;//重置下一层待打印节点数为0，重新计算
        }
    }
    return res;
}
```

### 思路二:BFS（适用于leetcode以数组输出）

### 代码二

```js
var levelOrder = function(root) {
    if(!root) return [];
    let queue = [];
    let res = [];
    queue.push(root);
    while(queue.length){
        let node = queue.shift();
        res.push(node.val);
        node.left && queue.push(node.left);
        node.right && queue.push(node.right);
    }
    return res;
};
```

