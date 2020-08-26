### 题目描述
小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列? Good Luck!

## 输出描述:双指针

```
设定两个指针，如果和大于sum，左指针向后移位，如果小于，右指针向后移位。
如果两个指针碰在一起，则跳出，
左指针一直小于sum的一半
```

### 思路一

```js
function FindContinuousSequence(sum)
{
    //滑动窗口
    if(sum < 2) return [];
    let left = 1, right = 2, s = 3, res = [];
    while(left <= Math.floor(sum/2)){//做指针永远小于和的一半
        if(s < sum){//当前的和太小，注意要先扩大窗口，再计算新的和
            right++;//右指针后移
            s += right;//和加上最新的
        }else if(s > sum){//缩小窗口，左指针后移
            s -= left;
            left++;
        }else{
            let path = [];
            for(let i = left; i <= right; i++){//注意i可以为右指针
                path.push(i)
            }
            res.push(path);
            if(left + 1 < right){//当left小于right,找到一个结果可以继续遍历其他结果
                s -= left;
                left++;
            }else{//当左指针与右指针交叉，跳出循环
                break;
            } 
        }
    }
    return res;
}
```



