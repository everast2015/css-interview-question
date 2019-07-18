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