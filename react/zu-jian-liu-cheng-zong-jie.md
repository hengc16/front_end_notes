# 组件流程总结

### 拆分组件

将一个界面进行组件化拆分。

### 实现静态组件

```text
render(){
       return (
            <div>
                tags
                tags
            </div> 
        )
}
```

### 实现数据初始化

```text
constructor (props) {
    super(props)
    this.state = {
        data: [1,2,3]
    }
}
```

* 初始化要在哪个组件里进行。
* 涉及到组件之间传值，传函数
* 每当从父组件拿值拿函数时， 要做propType的检查。而且要知道，你拿来的值是存在this.props里的。

### 实现动态交互

* 绑定事件监听
* 注意对新增函数的this 进行组件对象bind
* 状态更新必须通过setState\(\)这个函数来更新

### c-p 数据传递

* 在父组件设个key，传递一个回调函数。
* 父组件中定义回调函数。

遍历用map

删除用filter



