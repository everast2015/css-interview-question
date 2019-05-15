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

当上下相邻的两个块元素相遇时，如果上面的元素有下外边距`margin-bottom`，下面的元素有上外边距`margin-top`，则他们之间的垂直间距不是`margin-bottom`与`margin-top`之和，而是两者中的较大者。这种现象被称为相邻快元素垂直外边距的合并（也称为外边距塌陷）。

![垂直外边距的合并](https://github.com/yjn2015/css-interview/blob/master/img/css_margin_1.gif)

解决的方案，避免就好的了，例如设置一个边距就可以的了


### 嵌套快元素垂直外边距的合并

对于两个嵌套关系快元素，如果父元素没有上内边距及边框，则父元素的上外边距会与子元素的上外边距发生合并，合并后的外边距为两者中的较大者，即使父元素的上外边距为0，也会发生合并。

![垂直外边距的合并](https://github.com/yjn2015/css-interview/blob/master/img/css-margin.png)

解决方案：

1. 可以为父元素定义1像素的上边距或上内边距
2. 可以为父元素添加`overflow: hidden`

方法一：

```
    <div class="father">
        <div class="son"></div>
    </div>

    <style>
        .father {
            width: 200px;
            height: 200px;
            background-color: red;
            margin-top: 100px;
            border: 1px solid skyblue;
        }
        .son {
            width: 100px;
            height: 100px;
            background-color: blue;
            margin-top: 30px;
        }
    </style>
```

## 使用css制作向下小图标

方法：使用伪类的方法，然后设置`border-style` 的边可见，其他的隐藏，然后通过`transform: rotate()`旋转响应的角度即可。
```
.filter dt:after {
    content: '';
    display: inline-block;
    width: 4px;
    height: 4px;
    border: 1px solid #ccc;
    border-style: solid none none solid;
    transform: rotate(225deg);
    margin-left: .5rem;
}

```

## 手机端遮罩层的制作

手机端的遮罩层的制作的话，主要的就是高度的话，自适应屏幕的高度的，那么我们就采用`vh`高度的单位来制作的，然后采用定位的方式，可以把遮罩层放在相应的地方，搞定。

```
.active {
    position: absolute;
    top: 80px;
    left: 0;
    display: block;
    width: 100%;
    height: 100vh;
    background: rgba(0,0,0,0.3);
}
```