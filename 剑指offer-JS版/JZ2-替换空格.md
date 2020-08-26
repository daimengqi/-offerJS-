### 题目描述
请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。

### 思路一：正则

### 代码一

```js
var reg = new RegExp(/\s/g)
return str.replace(reg, '%20');
```

### 思路二:字符串+数组互相转换api

### 代码二

```js
  return str.split(' ').join('%20');
```

