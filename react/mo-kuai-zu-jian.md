# 模块&组件

### 模块： 

一个js文件。Modules。用来模块化开发，每个模块去实践自己的功能。提高代码可复用性，封装性，可扩展性。具体参照ood设计。

### 组件：

component， 通过组件来合成一个界面，如header，nav， cover，main-box，footer。 

每个组件都有自己的html, css, js, 和imgs，video，etc。 



面向对象-&gt; 面向模块-&gt;面向组件。 React用的时面向组件思想。

### 组件标签：

在React里，除了使用html自带标签，还可以时用组件标签，如&lt;MyComponent&gt;&lt;/MyComponent&gt;为了区分，所有的组件标签**首字母大写**。

### 组件编程分2步：

* **定义组件：**

  * 工场函数组件\(简单组件）：没有状态的组件。

```jsx
<script type="text/babel">
    //1.定义组件
    //工厂函数组件。
    function MyComponent(){
        return <h2> 工厂函数组件</h2>
    }
    //2. 渲染组件
    ReactDOM.render(<MyComponent/>, document.getElementById('container1'))
</script>

```

* es6类组件\(复杂组件\)

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

</head>
<body>
    <div id ="container1"></div>
    <div id ="container2"></div>


<script src="../js_link/react.development.js"></script>
<script src="../js_link/react-dom.development.js"></script>
<script src="../js_link/babel.min.js"></script>
<script type="text/babel">
    //1.定义组件
    //a.工厂函数组件。
    function MyComponent(){
        return <h2> 工厂函数组件</h2>;
    }
    //b. ES6类组件
    //创建component instance去调用render函数。
    class MyComponent2 extends React.Component{
        render(){
            return <h2> ES6类组件</h2>;
        }
    }
    //2. 渲染组件
    ReactDOM.render(<MyComponent/>, document.getElementById('container1'));
    ReactDOM.render(<MyComponent2/>, document.getElementById('container2'));
</script>
</body>
</html>
```

* **渲染组件标签：**

