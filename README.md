# CSS 面试题汇总

## CSS 权重两道题

1. 第一道题

```
<style>
    #father #son {
        color: blue;
    }
    #father p.c2 {
        color: black;
    }
    div.c1 p.c2 {
        color: red;
    }
    #father {
        color: green !important;
    }
</style>
<body>
    <div id="father" class="c1">
        <p id="son" class="c2">
            试问这行字体是什么颜色的？
        </p>
    </div>
</body>
```

这道题主要考察的就是`CSS` 权重的问题，我们知道
- ID 权重 `0,1,0,0`
- class 权重 `0,0,1,0`
- 标签 权重 `0,0,0,1`
- 继承权重为 0

所以我们得出结论：

1. #father #son 的权重为 `0,2,0,0`
2. #father p.c2 的权重为 `0,1,1,1`
3. div.c1 p.c2 的权重为 `0,0,2,2`
4.  #father 继承权重为0

所以最终的答案的字体的颜色是蓝色


2. 第二题

```
<style>
    #father {
        color: red;
    }
    p {
        color: blue;
    }
</style>

<body>
    <div id="father">
        <p>试问这行字体是什么意思？</p>
    </div>
</body>
```

解析：

因为 `#father` 选择器下的`p`元素是继承父元素的字体的颜色的属性的，所以继承的权重为0，而元素的权重为`0,0,0,1` 所以最终的字体的颜色是蓝色。


## 盒子模型

1. 外边距实现盒子居中

可以让一个盒子实现水平居中，需要满足一下两个条件：

1. 必须是快级元素
2. 盒子必须指定了宽度

然后给左右外边距都设置为`auto`，就可使快级元素居中。

### 清除盒子模型的内外边距

```
* {
    margin: 0;
    padding: 0;
}
```

注意，行内元素就只有左右内外边距的，是没有上下内外边距的。

### 外边距合并问题

使用`margin` 定义快元素的垂直外边距时，可能会出现外边距的合并。

### 相邻快元素垂直外边距的合并

当上下相邻的两个块元素相遇时，如果上面的元素有下外边距`margin-bottom`