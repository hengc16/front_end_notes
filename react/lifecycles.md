# lifeCycles

![](../.gitbook/assets/image%20%2839%29.png)

### 生命周期的回调函数（钩子）：

* 这些回调函数会在特定的时候被自动调用。
* 你重写与不重新他们都会被调用。
* 
### **命令式编程和声明式编程：**

jquery是命令式编程，所有步骤都是你来写，像先写一个问答题一样

而react是声明式编程，你只需要告诉他干什么，流程已经写好了， 像是填空题，把你想要的填到相应的位置。

### 效果

通过计时器来更改opacity，在click button后，实现删除当前div的操作。

这里用到了2个新的生命周期回调函数：

1. componentDidMount\(\) {} 如图，它属于加载后的生命周期函数，并且在更新阶段之前。我们可以将计时器绑定在这个生命周期阶段
2. componenetWillUnmount\(\){} 收尾阶段，解除计时器的绑定。

![](../.gitbook/assets/image%20%2840%29.png)

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
    //a.工厂函数组件。
    class App extends React.Component {
        //初始state
        constructor(){
            super()
            this.state = {
                opacity: 1
            }
            this.destroyComponent = this.destroyComponent.bind(this)
        }
        //加载好了后，写入计数器
        componentDidMount(){
            this.intervalId = setInterval(function() {
                let {opacity} = this.state;
                opacity -= 0.1
                if(opacity <= 0){
                    opacity = 1;
                }
                this.setState({opacity})
            }.bind(this),200)
        }
        //自定义函数，点击后触发，触发后删除主div
        destroyComponent(){
            ReactDOM.unmountComponentAtNode(document.getElementById("container1"))
        }
        //在生命周期结束前，去删除计时器
        componentWillUnmount(){
            clearInterval(this.intervalId)
        }

        render(){
            const {opacity} = this.state;
            return (
                <div>
                    <h2 style = {{opacity:opacity}}>我太难了</h2>
                    <button onClick = {this.destroyComponent}>我不活了</button>
                    </div>
            )
        }
        
    }

    ReactDOM.render(<App/>, document.getElementById('container1'));

</script>
</body>
</html>
```

