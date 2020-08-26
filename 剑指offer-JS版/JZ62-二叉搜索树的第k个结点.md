### 题目描述
给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8）  中，按结点数值大小顺序第三小结点的值为4。

### 思路：二叉搜索树中序遍历

### 代码

```js
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function KthNode(pRoot, k)
{
    let  res = [];
    if(!pRoot || k < 1)return null;
    //二叉搜索树中序遍历 就是 对树进行排序
    function inOrderTraverse(root){
        if(root.left != null){
            inOrderTraverse(root.left);
        }
        res.push(root);
        if(root.right != null){
            inOrderTraverse(root.right);
        }
    }
    inOrderTraverse(pRoot);
    return res[ k - 1];
}
```

