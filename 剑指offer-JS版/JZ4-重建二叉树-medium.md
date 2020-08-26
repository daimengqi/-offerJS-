### 题目描述

根据一棵树的前序遍历与中序遍历构造二叉树。

注意:
你可以假设树中没有重复的元素。

例如，给出

前序遍历 preorder = [3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]
返回如下的二叉树：

    3
   / \
  9  20
    /  \
   15   7

### 思路一：递归

```
1.前序遍历：根-左-右，中序遍历：左-根-右
2.前序遍历的第一个元素是根，中序遍历查找根的索引mid，mid左边为左子树(长度为m-1-0+ = m)，右边为右子树
3.对于前序遍历而言，索引[1, m]是左子树，后面的是右子树
```

### 代码一

```js
var buildTree = function(preorder, inorder) {
    if(!inorder.length) return null;
    let value = preorder[0] , mid = inorder.indexOf(value);//找到根节点，和根节点在中序遍历中的索引
    let root = new TreeNode(value);//根据值创建头节点
    root.left = buildTree(preorder.slice(1, mid + 1), inorder.slice(0, mid));//递归左子树
    root.right = buildTree(preorder.slice(mid+1), inorder.slice(mid+1));//递归右子树
    return root;
};
```





