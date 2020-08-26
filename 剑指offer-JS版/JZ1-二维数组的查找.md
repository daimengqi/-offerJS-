### 题目描述
在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

### 思路

分治:

从右上角(或者左下角)开始查找：
1.如果target更大，指针下移
2.如果target更小，指针左移

```js
//一、从左下角开始
function Find(target, array)
{
    // write code here
    //有顺序、左下角或者右上角做起始点
    let row = array.length - 1, col = 0;
    while(row >= 0 && col <= array[0].length - 1)
        if(target == array[row][col]){
            return true;
        }
        else if(target > array[row][col]){
            col++;
        }
        else{
            row--;
        }
    return false;
}


//二、从右上角开始
function Find(target, array)
{
    var row = 0;
    var col = array[0].length - 1;
    while(row < array.length && col >= 0){
        if (target == array[row][col]){
            return true;
        }
        else if (target > array[row][col]){
            row++;
        }
        else{
            col--;
        }
    }
    return false;
}
```

