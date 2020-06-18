# 模板语法\(template syntax\)

### 模板： 

动态的html页面，包含一些JS语法代码，双开号表达式和一些指令。

### 双开号表达式：

1\) 语法: {{exp}}

 2\) 功能: 向页面输出数据 

3\) 可以调用对象的方法

### 指令：

以v-开头的自定义标签属性。

#### 指令1：强制数据绑定指令

```text
1) 功能: 指定变化的属性值
2) 完整写法: v-bind:xxx='yyy' //yyy 会作为表达式解析执行
3) 简洁写法: :xxx='yyy'
```

例如绑定img

```text
<img v-bind:src = "imgUrl">
或者
<img :src = "imgUrl">
```

#### 指令2：绑定事件监听

```text
1) 功能: 绑定指定事件名的回调函数
2) 完整写法:
v-on:keyup='xxx'
v-on:keyup='xxx(参数)'
v-on:keyup.enter='xxx'
3) 简洁写法:
@keyup='xxx'
@keyup.enter='xxx'
```

```text
<h2>3. 指令二: 绑定事件监听</h2>
<button v-on:click="handleClick">点我</button>
<button @click="handleClick">点我2</button>
```

注意事件触发的回调函数要写在methods里。

```javascript
new Vue({
    el: '#app',
    data: {// data 的所有属性都会成功vm 对象的属性, 而模板页面中可以直接访问
        msg: 'I love CSGO',
        url: 'http://www.google.com'
    },
    methods: {
        handleClick () {
            alert('处理点击')
        }
    }
})
```

