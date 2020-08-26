### 题目描述

给定一个数组 nums 和滑动窗口的大小 k，请找出所有滑动窗口里的最大值。

示例:

输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 

  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7

### 思路一:暴力遍历

循环遍历数组，一个个找道滑动窗口，再找窗口中最大值，存入结果数组

### 代码一

```js
function maxInWindows(num, size)
{
    if(size === 0) return [];
    let res = [], window = [];
    for(let i = 0; i < num.length - size + 1; i++){
        window = num.slice(i, i + size);
        res.push(Math.max(...window))
    }
    return res;
}
```



