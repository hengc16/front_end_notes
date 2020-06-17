# hello world

创建一个vue 的实例

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>01_HelloWorld</title>
</head>
<body>

<!--
  1. 引入Vue.js
  2. 创建Vue对象
    el : 指定根element(选择器)
    data : 初始化数据(页面可以访问)
  3. 双向数据绑定 : v-model
  4. 显示数据 : {{xxx}}
  5. 理解vue的mvvm实现
-->

<!--模板-->
<div id="test"> <!--view mvvm 里的v-->
  <input type="text" v-model="msg"><br><!--指令-->
  <input type="text" v-model="msg"><!--指令-->
  <p>hello {{msg}}</p><!--大括号表达式-->
</div>

<script type="text/javascript" src="../js/vue.js"></script>
<script type="text/javascript">
  // 创建Vue instance
  const vm = new Vue({ // 配置对象 options  mvvm 里的vm
    // 配置选项(option)
    el: '#test',  // element: 指定用vue来管理页面中的哪个标签区域
    data: {  // 数据（model） 也就是mvvm的 m
      msg: 'hello world'
    }
  })
</script>
</body>
</html>
```

### mustache插值表达式

```text
1) 语法: {{exp}}
2) 功能: 向页面输出数据
3) 可以调用对象的方法
```

### MVVM为 数据代理\(MVVM.js\)

```text
model: 模型， 数据对象（data）
view：视图，模板界面
viewModel：视图模型（vue实例）
```



### **双向数据绑定 v-model**

```text
	1). 双向数据绑定是建立在单向数据绑定(model==>View)的基础之上的
	2). 双向数据绑定的实现流程:
      	* 在解析v-model指令时, 给当前元素添加input监听
      	* 当input的value发生改变时, 将最新的值赋值给当前表达式所对应的data属性
```

### 声明式 vs 命令式

```text
1.有别于jQuery的命令式，要告诉程序在哪监听，在哪显示。告诉计算机how to do

2.Vue采用的是声明式，只需要给对正确的声明，告诉计算机你的目的，繁琐的代码不需要你去考虑。
告诉计算机what to do。
```



