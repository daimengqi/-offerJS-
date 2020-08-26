### 题目描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

### 思路一：找出规律fn = 2*f(n-1)

### 代码一

```js
function jumpFloorII(number)
{
    // write code here
    if(number <= 0){
        return 0;
    }else{
        return Math.pow(2, number - 1);
    }
}
```

### 思路二：递归

### 代码二：

```js
function jumpFloorII(number)
{
    if(number === 1)return 1;
    return jumpFloorII(number - 1) * 2;
}
```

