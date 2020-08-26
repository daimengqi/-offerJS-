### 题目描述

定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

### 思路一：辅助栈，栈顶元素为索引最后一个，求最小值只要维护更新一个min

### 代码一

```js
var stack = [];
function push(node)
{
    stack.push(node);
}
function pop()
{
    return stack.pop();
}
function top()
{
    return stack.length? stack[stack.length - 1]: null;
}
function min()
{
    let min = stack[0];
    for(let i = 1; i < stack.length; i++){
        if(stack[i] < min){
            min = stack[i];
        }
    }
    return min;
}
```
