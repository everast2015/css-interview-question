# CSS 面试题汇总

## CSS 权重五道题

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

