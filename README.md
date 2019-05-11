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