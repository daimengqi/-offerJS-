### 题目描述
把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

示例 1：

输入：[3,4,5,1,2]
输出：1

### 思路一

总体二分：

- if mid大于high, low = mid + 1
- if mid小于high, high = mid
- if mid等于high，此时 mid 可能处于左边的增区间，也可能处于右边的增区间，即最小元素不确定在它的左边还是右边所以 right-- ，换一个 nums[right] 再试
- 最小的值为low处的值

### 代码一

```js

function minNumberInRotateArray(rotateArray)
{
    if(!rotateArray.length) return 0;
    let [left, right] = [0, rotateArray.length - 1];
    while(left < right){
        let mid = Math.floor((left + right) >> 1);
        if(rotateArray[mid] > rotateArray[right]){
            left = mid + 1;
        }else if(rotateArray[mid] < rotateArray[right]){
            right = mid;//注意 ，mid可能为最小值
        }else{        //此时 mid 可能处于左边的增区间，也可能处于右边的增区间，即最小元素不确定在它的左边还是右边所以 right-- ，换一个 nums[right] 再试
            right--;
        }
    }
    return rotateArray[left];
}
```

### 思路二

数组从小到大排序再取第一个值

### 代码二

```js
function minNumberInRotateArray(rotateArray)
{
    rotateArray.sort((a, b) => a -b);
    return rotateArray[0];
}
```

### 思路三

分析数据，顺序排列的数组发现存在一个转折点，转折点即为最小值

### 代码三

```js
function minNumberInRotateArray(rotateArray)
{
    if(rotateArray.length === 0) return 0;
    for(let i = 0; i < rotateArray.length; i++){
        if(rotateArray[i] > rotateArray[i + 1]){
            return  rotateArray[i + 1];
        }
    }
}
```

