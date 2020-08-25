# 跨域问题

### 跨域（非同源策略请求）：

* 同源策略请求：  ajax/ fetch
* 跨域请求。

由于前后端分离，前端的端口在localhost:3000

后端的服务器端口在localhost:8080 

### 如何区分：

* 域名
* 协议
* 端口号

以上3者都一样为同源， 只要有一个不同就是跨域。

请求第三方开源api也是跨域

### 解决方法:

### **Jsonp：**

* 利用script标签无跨域限制来发请求
* 缺点：
  * 需要服务器端的支持
  * 不能传post

![](../.gitbook/assets/image%20%2873%29.png)

### CORS跨域资源共享：

* 客户端发送请求
* 服务器端处理请求头
  * 缺点： header头access-control-allow-origin只能支持一个源，或者\*号
  * 如果设置为\*， 就不能允许携带cookie

配置config：

![](../.gitbook/assets/image%20%2875%29.png)

用中间件来改写请求头

![](../.gitbook/assets/image%20%2876%29.png)

### http proxy 代理

* 一般用来配合webpack  webpack-dev-server



在webpack.config里加proxy

![](../.gitbook/assets/image%20%2874%29.png)

### nginx做反向代理：

* 不需要前端
* 都是服务器部署

### 其他方法：

* **用iframe**
  * iframe里的contentwindow.postMessage（）发请求
  * 用window.onmessage（ev） 接收请求
  * 用ev.source.postMessage\(ev.data + '@@@' , ev.origin\) 来发请求。
* 
