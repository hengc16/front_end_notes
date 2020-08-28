# json-server

* 一个可以创建fake rest api的包

{% embed url="https://github.com/typicode/json-server" %}

* 先全局安装json-server
* 在主路径下创建db.json来模拟database
* 启动json-server

假如数据库长这样

![](../.gitbook/assets/image%20%2896%29.png)

我们对外暴露的api为

* /posts
* /comments
* /profile 

因为他们是restful的，

所以我们可以分别对每个api做增删改查

### 用axios去测试rest api 的crud

![](../.gitbook/assets/image%20%2892%29.png)

![](../.gitbook/assets/image%20%2894%29.png)

![](../.gitbook/assets/image%20%2887%29.png)

![](../.gitbook/assets/image%20%2890%29.png)

