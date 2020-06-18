# 事件处理\(event handling）

通常是用v-on 来对dom事件进行监听， 触发时运行相关js代码。

但是当事件处理逻辑变的复杂，我们就不能将js代码写在v-on指令中了，我们可以让v-on去调用一个函数。

```jsx
<div id="example-2">
  <!-- `greet` 是在下面定义的方法名 -->
  <button v-on:click="greet">Greet</button>
</div>

var example2 = new Vue({
  el: '#example-2',
  data: {
    name: 'Vue.js'
  },
  // 在 `methods` 对象中定义方法
  methods: {
    greet: function (event) {
      // `this` 在方法里指向当前 Vue 实例
      alert('Hello ' + this.name + '!')
      // `event` 是原生 DOM 事件
      if (event) {
        alert(event.target.tagName)
      }
    }
  }
})
```

### 事件修饰符

在事件处理时，我们需要防止时间冒泡，就需要调用event.stopPropagation\(\)，vue则提供了时间修饰符。

```jsx
  <div style="width: 200px;height: 200px;background: red" @click="test1">
    <div style="width: 100px;height: 100px;background: blue" @click.stop="test2"></div>
    
    new Vue({
    el: '#example',
    data: {

    },
    methods: {
      test1 () {
        alert('out')
      },
      test2 () {
        alert('inner')
      }
    }
  })
```

![](../.gitbook/assets/image%20%2813%29.png)

 如果不阻止时间冒泡的话，当你点击小的blue方块时，会触发test1，和test2 这2个事件。我们可以通过对test2这个事件添加stop这个修饰符来阻止时间冒泡。

另外一个常用的event.preventDefault\(\). 阻止事件默认行为。 在vue里则是对时间添加.prevent这个修饰符就好了。

还有就是@keyup.enter对应了之前的event.keyCode===13 来判断用户是否type了enter键。



