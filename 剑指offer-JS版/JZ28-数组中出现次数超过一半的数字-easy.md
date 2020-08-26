### 题目描述
数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。



示例 1:

输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
输出: 2

### 思路二:哈希表

遍历数组，依次存储数组中独立元素的个数，最后计算个数是否大于数组的一半,不存在则为0

### 代码二

```js
function MoreThanHalfNum_Solution(numbers)
{
    let map = {};
    for(let i = 0; i < numbers.length; i++){
        if(map[numbers[i]]){
            map[numbers[i]]++;
        }else{
            map[numbers[i]] = 1;
        }
    }
    for(let key in map){
        if(map[key] > (numbers.length >> 1)){
            return key;
        }
    }
    return 0;
}
```

