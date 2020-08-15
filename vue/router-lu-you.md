# router 路由

### 介绍

* 根据不同的url地址来显示不同的内容或页面
* router其实就是对history的一个封装。
* when：
  * single page 开发
* 优点：
  * 用户体验好，不需要每次都从服务器拿一整个页面
  * 速度快，局部刷新
* 缺点：
  * 不利于SEO
  * 使用浏览器的前进后退都是一个新的request，没有合理利用缓存
  * 单页面无法记住滚动的位置，

### 2种方式：

&lt;router-link&gt;&lt;/router-link&gt; 当a标签来用

&lt;router-view&gt;&lt;/router-view&gt;渲染， 配合跳转来用。

### 2种路由模式：

mode: 'hash'

需要通过 8080/\#/user/admin 来访问， 

mode: 'history'

通过 8080/user/admin   比较直接。

### 4种路由：

### 动态路由

![](../.gitbook/assets/image%20%2863%29.png)

### 嵌套式路由

* 类似于页面内部的跳转
* 二级路由
* 子组件 array

![](../.gitbook/assets/image%20%2868%29.png)

![](../.gitbook/assets/image%20%2866%29.png)

注意要写全，并且跟子路由的path匹配

### 编程式路由

![](../.gitbook/assets/image%20%2865%29.png)

* 注意$router 和$route的区别
* query 和 params的区别
* query拿取 name?a= 123 
* params拿取router传递的 goods/:goodsId 里的goodsId



### 命名路由和命名视图



![](../.gitbook/assets/image%20%2871%29.png)

不经常用， 因为可以自己切分。



