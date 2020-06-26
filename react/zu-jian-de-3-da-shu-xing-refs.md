# 组件的3大属性: refs

1\)         组件内的标签都可以定义ref属性来标识自己

a.         &lt;input type="text" ref={input =&gt; this.msgInput = input}/&gt;

b.         回调函数在组件初始化渲染完或卸载时自动调用

2\)         在组件中可以通过this.msgInput来得到对应的真实DOM元素

3\)         作用: 通过ref获取组件内容特定标签对象, 进行读取其相关数据



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
    <div id = "container2"></div>

<script src="../js_link/react.development.js"></script>
<script src="../js_link/react-dom.development.js"></script>
<script src="../js_link/babel.min.js"></script>
<script type="text/babel">
    //定义组件
    class MyComponent extends React.Component{
        constructor (props){
            super(props)
            this.showInput = this.showInput.bind(this)
            this.handleblur = this.handleblur.bind(this)
        }
        showInput(){
            // do 提示 input的内容。 如何拿到input的内容
            // 通过ref来access input。将当前input 保存到组件对象this， 的input里
            alert(this.input.value)
        }
        handleblur(event){
            //当前事件的event target 为input。 他的值
            alert(event.target.value)
        }
        render(){
            return (
                <div>
                    <input type="text" ref = {a => this.input = a}/>
                    <button onClick ={this.showInput}>提示</button>
                    <input type="text" placeholder ="onblur 提示" onBlur ={this.handleblur}/>
                </div>
            )
        }
    }
    //渲染组件标签
    ReactDOM.render(<MyComponent/>, document.getElementById("container1"));

</script>
</body>
</html>
```



