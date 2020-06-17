# 计算属性（computed\) 和监视属性（watch）

### 为什么要有computed property

模板内的表达式非常便利，但是设计它们的初衷是用于简单运算的。在模板中放入太多的逻辑会让模板过重且难以维护。如：

```javascript
<div id="example">
  {{ message.split('').reverse().join('') }}
</div
```

### 计算属性

为了更好的可读性，我们应当把复杂的逻辑放在它该在的地方，也就是在computed property那里。

```javascript
<div id="example">
  <p>Original message: "{{ message }}"</p>
  <p>Computed reversed message: "{{ reversedMessage }}"</p>
</div>
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
```

计算属性（computed\) vs methods：

对于上面的反转string我们完全可以将它写在methods里，可是为什么我们要写到computed里呢。

因为computed是基于响应式依赖进行缓存的，要在响应发生改变时才会去从新求值， 也就意味着只要message不变，多次访问reversedMessage只会返回之前的结果，不用再次执行函数了。

隐患就是当你把Data.now\(\)放入computed，他将不在更新。

```javascript
computed: {
  now: function () {
    return Date.now()
  }
}
```

### 监听属性（watch\)

配置监听指定属性，如果发生改变自己调用相应的回调函数。在下面的例子里，当firstname 或lastname 发生改变时， 会自动调用回调函数，更新fullname里的值。

### 计算属性高级

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>03_计算属性和监视</title>
</head>
<body>
<!--
1. 计算属性
  在computed属性对象中定义计算属性的方法
  在页面中使用{{方法名}}来显示计算的结果
2. 监视属性:
  通过通过vm对象的$watch()或watch配置来监视指定的属性
  当属性变化时, 回调函数自动调用, 在函数内部进行计算
3. 计算属性高级:
  通过getter/setter实现对属性数据的显示和监视
  计算属性存在缓存, 多次读取只执行一次getter计算
-->
<div id="demo">
  姓: <input type="text" placeholder="First Name" v-model="firstName"><br>
  名: <input type="text" placeholder="Last Name" v-model="lastName"><br>
  <!--fullName1是根据fistName和lastName计算产生-->
  姓名1(单向): <input type="text" placeholder="Full Name1" v-model="fullName1"><br>
  姓名2(单向): <input type="text" placeholder="Full Name2" v-model="fullName2"><br>
  姓名3(双向): <input type="text" placeholder="Full Name3" v-model="fullName3"><br>

  <p>{{fullName1}}</p>
  <p>{{fullName1}}</p>
</div>

<script type="text/javascript" src="../js/vue.js"></script>
<script type="text/javascript">
  const vm = new Vue({
    el: '#demo',
    data: {
      firstName: 'A',
      lastName: 'B',
       fullName2: 'A-B'
    },

    // 计算属性配置: 值为对象
    computed: {
      fullName1 () { // 属性的get()
        console.log('fullName1()', this)
        return this.firstName + '-' + this.lastName
      },

      fullName3: {
        // 当获取当前属性值时自动调用, 将返回值(根据相关的其它属性数据)作为属性值
        get () {
          console.log('fullName3 get()')
          return this.firstName + '-' + this.lastName
        },
        // 当属性值发生了改变时自动调用, 监视当前属性值变化, 同步更新相关的其它属性值
        set (value) {// fullName3的最新value值  A-B23
          console.log('fullName3 set()', value)
          // 更新firstName和lastName
          const names = value.split('-')
          this.firstName = names[0]
          this.lastName = names[1]
        }
      }
    },

    watch: {
      // 配置监视firstName
      firstName: function (value) { // 相当于属性的set
        console.log('watch firstName', value)
        // 更新fullName2
        this.fullName2 = value + '-' + this.lastName
      }
    }
  })

  // 监视lastName
  vm.$watch('lastName', function (value) {
    console.log('$watch lastName', value)
    // 更新fullName2
    this.fullName2 = this.firstName + '-' + value
  })

</script>
</body>
</html>
```

