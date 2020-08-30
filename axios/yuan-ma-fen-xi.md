# 源码分析

![](../.gitbook/assets/image%20%28109%29.png)

axios是一个函数

axios是由createInstance这个函数调用来的

![](../.gitbook/assets/image%20%28111%29.png)

这个函数里return的是一个新的函数instance 去调用request。

