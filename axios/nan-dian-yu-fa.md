# 难点语法

![](../.gitbook/assets/image%20%28108%29.png)

axios的2次封装：

主要解决多个config的情况。不同的instances对应不同的配置

const instance = axios.create\({config}\);

