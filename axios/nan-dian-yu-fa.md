# 难点语法

![](../.gitbook/assets/image%20%28109%29.png)

axios的2次封装：

* 主要解决多个config的情况。不同的instances对应不同的配置
* const instance = axios.create\({config}\);
* 这里的instance像是axios的一个分身， 可以当函数被调用，也可以当对象直接调用它的方法。



