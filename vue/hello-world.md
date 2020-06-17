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
1.通过一个对象代理对另一个对象中属性的操作(读/写)
2.通过vm对象来代理data对象中所有属性的操作
3.好处: 更方便的操作data中的数据
4.基本实现流程
	1). 通过Object.defineProperty()给vm添加与data对象的属性对应的属性描述符
	2). 所有添加的属性都包含getter/setter
	3). 在getter/setter内部去操作data中对应的属性数据
```



### **双向数据绑定 v-model**

```text
	1). 双向数据绑定是建立在单向数据绑定(model==>View)的基础之上的
	2). 双向数据绑定的实现流程:
      	* 在解析v-model指令时, 给当前元素添加input监听
      	* 当input的value发生改变时, 将最新的值赋值给当前表达式所对应的data属性
```



