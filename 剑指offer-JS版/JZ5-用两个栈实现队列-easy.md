### 题目描述
用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。

### 思路
一个栈用来存储
pop时弹出stack2，stack2为空，pop出stack1存储在stack2中

注意题目概述，这边用到的是构造函数，要写进原型链中

### 代码

```js
var stack1 = [], stack2 = [];
function push(node)
{
    stack1.push(node);
}
function pop()
{
    if(stack2.length === 0){
        if(stack1.length === 0){
            return null;
        }else{
            let len = stack1.length;
            for(let i = 0; i < len; i++){
                stack2.push(stack1.pop());
            }
            return stack2.pop();
        }
    }else{
        return stack2.pop();
    }
}
```

