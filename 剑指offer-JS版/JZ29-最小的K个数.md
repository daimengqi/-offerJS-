### 题目描述
输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4。

### 思路一：升序排序，切片

### 代码一

```js
function GetLeastNumbers_Solution(input, k)
{
    if(k > input.length) return [];
    input.sort((a, b) => a - b);
    return input.slice(0, k);
}
```





