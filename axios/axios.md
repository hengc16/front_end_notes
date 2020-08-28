# HTTP 相关

### HTTP：

![](../.gitbook/assets/image%20%28100%29.png)

![](../.gitbook/assets/image%20%28105%29.png)

### 请求报文：

1. **请求行：**
   1. method url
   2. GET/prudct\_detail?id=2
   3. POST/login

**2。请求头**

* 请求头的信息都是浏览器交给服务器去用的。

![](../.gitbook/assets/image%20%2896%29.png)

**3。请求体：**

username = tom&pwd = 123 对应 application/x-www-form-urlencoded  -&gt;统称url encoded格式

{"username":"tom", "pwd":123}   对应application/json   统称json格式

文本上传 -》  content-type： multipart/form-data格式

get是没有请求体的，只有post有

因为后台要解析请求体里的内容，所以你要通过content-type来告诉他body里是什么格式，json还是字符串。

### 响应报文：

 **响应状态行：**

* status, status text  200， 404， 500 .。。

![](../.gitbook/assets/image%20%28106%29.png)

**多个响应头：**

![](../.gitbook/assets/image%20%28102%29.png)

**响应体：**

* html 文本/json / js/ css/img。。。

### API分类：

![](../.gitbook/assets/image%20%2890%29.png)

