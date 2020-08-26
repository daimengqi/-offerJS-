### 题目描述

在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组,求出这个数组中的逆序对的总数P。并将P对1000000007取模的结果输出。 即输出P%1000000007

## 输入描述:

```
题目保证输入的数组中没有的相同的数字数据范围：	对于%50的数据,size<=10^4	对于%75的数据,size<=10^5	对于%100的数据,size<=2*10^5
```

示例1

## 输入

[复制](javascript:void(0);)

```
1,2,3,4,5,6,7,0
```

## 输出

[复制](javascript:void(0);)

```
7
```

### 思路一

```
1、归并排序
2、关键是遍历左边部分时，当左边中的某个元素的值大于右边部分的值，则该元素后面的所有元素也都大于右边部分，即满足逆序对。总共有leftLen - 1 - i +1 = leftLen - i个逆序对
```

### 代码一

```js
function InversePairs(data)
{
    // write code here
    let sum = 0;
    mergeSort(data);
    return sum %1000000007 ;
    
    function mergeSort(arr){
        if(arr.length < 2)return arr;
        let mid = Math.floor(arr.length >> 1);
        let left = arr.slice(0, mid);
        let right = arr.slice(mid);
        return merge(mergeSort(left), mergeSort(right));
    }
    
    function merge(left, right){
        let res = [];
        let leftLen = left.length;
        let rightLen = right.length;
        let len = leftLen + rightLen;
        for(let index = 0, i = 0,  j = 0; index < len; index++){
            if(left[i] <= right[j]){
                res[index] = left[i++];
            }else if(left[i] > right[j]){
                res[index] = right[j++];
                sum += leftLen - i; //归并排序中唯一添加代码
            }else if(i >= leftLen){
                res[index] = right[j++];
            }else{
                res[index] = left[i++];
            }
        }
        return res;
    }
}
```



