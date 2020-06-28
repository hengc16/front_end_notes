# component composing 多个组件组合

![](../.gitbook/assets/image%20%2838%29.png)

做一个todo list， 

需求： 显示所有todo list， 输入文本， 点击按钮显示到list首位，并清除输入的文本。

### 功能界面的组件化编码流程

1. 拆分组件：拆分界面，抽取组件
2. 实现静态组件： 使用组件实现静态界面效果
3. 实现动态组件：
   1. 动态组件的初始化数据
   2. 交互功能（即绑定监听）

### 实现静态组件：

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



<script src="../js_link/react.development.js"></script>
<script src="../js_link/react-dom.development.js"></script>
<script src="../js_link/babel.min.js"></script>
<script type="text/babel">
    //1.定义组件
    class App extends React.Component{
        render(){
            return (
                <div>
                    <h1> todo list </h1>
                    <Add></Add>
                    <List></List>
                </div>
            )
        }
    }
    
    //b. 子类组件
    class Add extends React.Component{
        render(){
            return (
                <div> 
                   <input type="text"/>
                   <button>add</button> 
                </div>
            )
        }
    }
    class List extends React.Component{
        render(){
            return (
                <div>
                    <ul>
                        <li>xxx</li>
                        <li>xxx</li>
                    </ul>
                </div>
            )
        }
    }
    //2. 渲染组件
    ReactDOM.render(<App/>, document.getElementById('container1'));
</script>
</body>
</html>
```

### 实现动态组件：

先实现初始化数据再交互。



