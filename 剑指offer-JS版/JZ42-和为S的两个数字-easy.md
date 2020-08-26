### 题目描述

输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。

## 输出描述:

```
对应每个测试案例，输出两个数，小的先输出。
```

### 思路一:双指针

```
1、左右指针分别从数组头部和尾部开始移动
2、根据规律，同样和为s的两个数，相隔越远，乘积越小
3、因而用res二维数组存储一对对的两个数的话，结合左右指针，第一次找到的一对就是乘积最小的，直接break跳出循环，输出res即可。
```

### 代码一

```js
function FindNumbersWithSum(array, sum)
{
    let len = array.length;
    if(len < 2) return [];
    let left = 0, right = len - 1, res = [];
    while(left < right){
        if(array[left] > sum) return [];
        let s = array[left] + array[right];
        if(s === sum){
            res.push(array[left], array[right]);//递增排序，按要求左边的先进入res
            break;//因为只要找乘积最小的，那么left和right相隔最远乘积最小，直接跳出循环即可
        }else if(s < sum){
            left++;
        }else{
            right--
        }
    }
    return res;
}
```



