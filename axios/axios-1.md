# axios

![](../.gitbook/assets/image%20%28110%29.png)

注意请求/响应拦截器， intercept request and response

* request interceptor是在发请求前执行
  * 如在发请求前对要发出去的做数据的处理
* response interceptor 是在拿到响应数据之后进行统一处理

服务器端和浏览器端都可以用axios

* 在服务器段用axios就只是http请求了
* 在浏览器端发的是http中的ajax请求。
* axios可以作为函数来被调用，如调制config
* 也可以作为对象来被调用，如axios.get\(url,\[config\]\) 
  * 这种其实是为了方便，axios做了一层封装，也叫函数糖，语法糖。

![](../.gitbook/assets/image%20%28108%29.png)

![](../.gitbook/assets/image%20%28109%29.png)

