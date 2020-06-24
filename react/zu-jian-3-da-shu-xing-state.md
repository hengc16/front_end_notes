# 组件3大属性-state

state是组件最重要的属性，值是对象\(包含多个数据\)

组件被称为'状态机', 通过更新组件的state 来更新对应界面的显示（rerender）

对状态的操作分三种：

初始化状态:

```jsx
constructor(props){
    super(props)
    this.state = {
        stateProp1: value1,
        stateProp2: value2
    }
}
```

读取某个状态值

```jsx
this.state.statePropertyName
```

更新状态-&gt;组件界面更新

```jsx
this.setState({
    stateProp1 : value1,
    stateProp2 : value2
})
```

 See the Pen [react-state-example](https://codepen.io/hengc16/pen/oNbwBxZ) by Heng Cai \([@hengc16](https://codepen.io/hengc16)\) on [CodePen](https://codepen.io).

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
    //b. ES6类组件
    class Switch extends React.Component{
        //创建一个state
        constructor(Props){
            super(Props)
            //初始化state
            this.state = {
                isOn : false
            }
            //将新增方法中的this强制绑定为组件对象
            this.handleClick = this.handleClick.bind(this)
            
        }
        //新添加的方法，默认this为undefined， 
        handleClick(){
            //得到状态
            const isOn = !this.state.isOn
            //更新状态
            this.setState({isOn})
        }
        //重写组件内的方法
        render(){
            //读取状态  用到了ES6的对象的解构赋值
            const {isOn} = this.state;
            return <h2 onClick = {this.handleClick}>{isOn?'黑':'白'}</h2>
        }
    }
    //2. 渲染组件
    ReactDOM.render(<Switch/>, document.getElementById('container1'));
</script>
</body>
</html>
```

