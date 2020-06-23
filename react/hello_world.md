# hello\_world

1. 引入相关包的cdn link。 
2. 将要编辑的JS 文件text设为babel
3. 在html设置好要插入的div container，和id
4. 在js文件里，建想要插入的元素
5. 用jsx来创建虚拟dom，如 var vDom = &lt;h1 id={myId}&gt; {myMsg} &lt;/h1&gt;
   1. 这里{}来绑定之前设置的var，var可以被动态改变
6. 使用ReactDOM.render\(vDom, document.getElementById\("id"\)\)来渲染创建的虚拟DOM。

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

</head>
<body>
    <div id ="upper"></div>
    <div id = "lower"></div>

<script src="../learn_react/js_link/react.development.js"></script>
<script src="../learn_react/js_link/react-dom.development.js"></script>
<script src="../learn_react/js_link/babel.min.js"></script>
<script type="text/babel">
    const myId = "myid";
    const myMsg = "Hello World";
    //创建虚拟DOM
    const vDom = <h1 id = {myId.toLowerCase()}> {myMsg.toLowerCase()}</h1>;
    const vDomUpper = <h1 id = {myId.toUpperCase()}> {myMsg.toUpperCase()}</h1>;
    //渲染虚拟DOM
    ReactDOM.render(vDom, document.getElementById("lower"));
    ReactDOM.render(vDomUpper, document.getElementById("upper"))

</script>
</body>
</html>
```

![](../.gitbook/assets/image%20%2834%29.png)

![](../.gitbook/assets/image%20%2835%29.png)

**虚拟DOM vs 真实DOM:**  
 1.  虚拟DOM比较轻，只存它需要的信息

2. 虚拟DOM内容发生改变，页面不会更新， 真实DOM内容更新，页面也会随之更新。

**创建的虚拟DOM对象: const vDom = &lt;h1&gt; hello JSX &lt;/h1&gt;;** 

它不是字符串，所以不能加“ ”， 它最终产生的是一个JS 对象。

基本语法：

* 以&lt; 开头的代码，为标签语法解析。如 &lt;h1&gt; &lt;p&gt; &lt;div&gt; 等
* 以{ 开头的代码，为JS语法解析， 如{myid.toUpperCase\(\)}
* 渲染虚拟DOM: ReactDOM.reander\( **virtualDOM, containerDOM**\) 将vDOM渲染到container那里。

这里为了测试语法，都是现场编译的， 真正到做项目，是先编译好，再打包上传的，所以运行效率会提高。

