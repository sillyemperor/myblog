Title: Python数组复制的陷阱
Date: 2019-06-04
Category: Python
Tags: Python



说是陷阱其实有点标题党，其实是最近的一次DEBUG结果。先看代码：

>>a=[1]*5

[1,1,1,1,1]

>>a[0]=2

[2,1,1,1,1]

这段代码的含义是复制了5个‘1’作为数组，修改其中一个元素后的结果。没毛病。但是：

>>b=[[1]*2]*2

[[1,1],[1,1]]

>>b[0][0]=2

[[2,1],[2,1]]

WTF！这显然不是我们想要的结果。其实问题也很简单，[object]*n=[object,object,...object]，也就是说复制的是对象的引用而不是值复制。例如：

>>o=object()

>>[o]*2

[<object object at 0x1083a7090>, <object object at 0x1083a7090>]

 可以看到，其实是同一个对象。