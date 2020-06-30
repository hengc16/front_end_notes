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

### 实现动态组件的数据初始化：

先实现初始化数据再交互。

数据保存在哪个组件内：   

看数据是某个组件需要\(给它\) 还是默写组件需要\(保存在共同父组件里\)

如上面例子 add 和list 都需要对todos这个数据进行操作，所以应该讲todos放在app这个父级组件里。

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
<script src="../js_link/prop-types.js"></script>
<script src="../js_link/babel.min.js"></script>
<script type="text/babel">
    //1.定义主组件
    //2. 实现数据初始化， 对应子组件的公共数据存父组件里。

    class App extends React.Component {
        constructor (props) {
            super(props)
            //初始化状态
            this.state = {
                todos: ['吃饭', '睡觉', '打豆豆']
            }
            //将新增方法中的this强制绑定为组件对象
            // this.add = this.add.bind(this)
        }
        render(){
            const {todos} = this.state
            return (
                <div>
                    <TodoAdd/>
                    <TodoList todos = {todos}/>
                </div>
            )
        }
    }
    //定义子组件
    class TodoAdd extends React.Component{
        render() {
            return (
                <div>
                    <input type="text"/>
                    <button>add</button>           
                </div>
            )
        }
    }

    //定义list 子组件
    class TodoList extends React.Component{
        render(){
            const {todos} = this.props
            return (
                <ul>
                    {
                        todos.map(
                            (todo, index) =>
                            <li key = {index}>{todo}</li>
                        )
                    }
                </ul> 
            )
        }
    }
    //检查list属性的type
    TodoList.propTypes = {
        todos : PropTypes.array.isRequired
    }

    //render component 
    ReactDOM.render(<App/>, document.getElementById("container1"))
</script>
</body>
</html>
```

### 交互：

问题： 需要在子组件中改变父组件的状态，怎么办？

首先子组件不能直接改变父组件的状态

状态在哪个组件，更新状态的行为就应该在哪个组件内。

还要注意，如果要更新状态，不能直接更新数据本身，而是要调用setState去更新state



父组件创建完state 更新函数后，可以像传数据一样把函数传给子组件。这里add = {this.add} 的this，如果不加，它会在当前区域里找add，如果加了 就是在组件对象这个范围找add。

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
<script src="../js_link/prop-types.js"></script>
<script src="../js_link/babel.min.js"></script>
<script type="text/babel">
    //1.定义主组件
    //2. 实现数据初始化， 对应子组件的公共数据存父组件里。

    class App extends React.Component {
        constructor (props) {
            super(props)
            //初始化状态
            this.state = {
                todos: ['吃饭', '睡觉', '打豆豆']
            }
            // 将新增方法中的this强制绑定为组件对象
            this.add = this.add.bind(this)
        }
        add(todo){
            const {todos} = this.state
            todos.unshift(todo)
            this.setState({todos})
        }
        render(){
            const {todos} = this.state
            return (
                <div>
                    <TodoAdd count = {todos.length} add = {this.add}/>
                    <TodoList todos = {todos}/>
                </div>
            )
        }
    }
    //定义子组件
    class TodoAdd extends React.Component{
        //一旦定义新的函数，要开个构造器去绑定 函数到组件对象
        constructor(props){
            super(props) 
            this.handleClick = this.handleClick.bind(this)
        }
        handleClick(){
            //1.读取input
            const todo = this.todoInput.value.trim()
            //2. 检查合法性
            if(!todo){
                return
            }
            //3. 添加, 调用传过来的props里的add函数。
            this.props.add(todo)
            //4. 清除input里的text
            this.todoInput.value = ''
        }
        render() {
            return (
                <div>
                    <input type="text" ref ={input => this.todoInput = input}/>
                    <button onClick = {this.handleClick}>add{this.props.count + 1}</button>           
                </div>
            )
        }
    }
    // todoAdd 接收 count  要检查一下类型
    // 又接收了add 函数 检查一哈
    TodoAdd.propTypes = {
        count : PropTypes.number.isRequired,
        add: PropTypes.func.isRequired
    }

    //定义list 子组件
    class TodoList extends React.Component{
        render(){
            const {todos} = this.props
            return (
                <ul>
                    {
                        todos.map(
                            (todo, index) =>
                            <li key = {index}>{todo}</li>
                        )
                    }
                </ul> 
            )
        }
    }
    //检查list 接收的todos的type
    TodoList.propTypes = {
        todos : PropTypes.array.isRequired
    }

    //render component 
    ReactDOM.render(<App/>, document.getElementById("container1"))
</script>
</body>
</html>
```

