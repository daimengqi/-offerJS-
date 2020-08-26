### 题目描述
大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0，第1项是1）。

n<=39

### 思路一：构造斐波那契数组前两位

### 代码一

```js
function Fibonacci(n)
{
    // write code here
    let res = [0, 1];
    for(let i = 2; i <= n; i++){
        //res[i] = res[i - 1] + res[i - 2];
        res.push(res[i - 1] + res[i - 2]);
    }
    return res[n];
}
```

### 思路二：用两个变量进行维护，不断更新变量

### 代码二：

```js
function Fibonacci(n)
{
    if(n === 0) return 0;
    if(n === 1) return 1; 
    let a = 0 ,b = 1;
    let result;
    for(let  i = 2; i <= n; i++){
        result = a + b;
        a = b;
        b = result;
    }
    return result;
}
```

