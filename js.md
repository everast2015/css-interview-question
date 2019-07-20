# js面试题

## 数组

1. 求数组中的最大值

思路：
1. 声明一个保存最大元素的变量max.
2. 默认最大值取数组中的第一个
3. 遍历这个数组，把里面每个数组元素和`max`像比较
4. 如果这个数组元素大于`max`就把这个数组元素存到`max`里面，否则继续下一轮比较。
5. 最后输出这个`max`

```js
<script>
        var arr = [2, 4, 6, 8, 1, 10, 101, 15, 3];
        var max = arr[0];
        for (let index = 0; index < arr.length; index++) {
            if (arr[index] > max) {
                max = arr[index]
            }
        }
        document.write(max); 
        // 最后输出的是101
</script>
```

2. 求数组中大于10的元素，并把它选出来，放在新数组

思路：
1. 将数组`[2,0,6,1,77,0,52,0,25,7]` 中大于等于10的元素选出来，放入新数组
2. 声明一个新数组用来存放数据`newArr`
3. 遍历原来的旧数组，找出大于等于10的新元素。
4. 依次追加给新数组newArr

```js
var arr = [2,0,6,1,77,0,52,0,25,7];
var newArr = [];
var j = 0;
for(var i = 0; i< arr.length; i++){
    if(arr[i] > 10) {
        // 新数组应该从0开始，依次类推
        newArr[j] = arr[i]
        j++
    }
}
console.log(newArr); // [77,52,25]
```

3. 删除指定数组中的元素

要求：将数组`[2,0,6,1,77,0,52,0,25,7]` 中的0去掉后，形成一个不包含0的数组。
方法一：
```js
   var arr = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
   var newArr = [];
   var j = 0;
   for (var i = 0; i < arr.length; i++) {
        if (arr[i] != 0) {
        // 新数组应该从0开始，依次类推
            newArr[j] = arr[i]
            j++
            }
        }
    console.log(newArr); // [2, 6, 1, 77, 52, 25, 7]
```

4. 翻转数组
要求：将数组`['red','green','blue','pink','purple']` 内容反转存放
1. 声明一个新数组`newArr`
2. 把旧数组索引号第四个取过来`(arr.length - 1)`，给新数组索引号第0个元素`(newArr.length)`
3. 我们采用递减的方式 `i--`