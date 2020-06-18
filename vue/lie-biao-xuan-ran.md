# 列表渲染\(list rendering\)

通过v-for 来遍历persons这个数组，并对其做修改。

这里用到了splice\(\). 这就涉及到了变更方法

#### [变更方法](https://cn.vuejs.org/v2/guide/list.html#%E5%8F%98%E6%9B%B4%E6%96%B9%E6%B3%95) <a id="&#x53D8;&#x66F4;&#x65B9;&#x6CD5;"></a>

Vue 将被侦听的数组的变更方法进行了包裹，所以它们也将会触发视图更新。这些被包裹过的方法包括：

* `push()`
* `pop()`
* `shift()`
* `unshift()`
* `splice()`
* `sort()`
* `reverse()`

vue重写了这几个方法，让他们做到对数组内部元素的监听。

我们可以调用上面这些方法来对内在element做更新，随后页面也会reactive的去更新。

如下面例子里，我们通过对persons\[index\] = newP 来更新当前index为新的element。 虽然element被重新赋值了， 但是我们页面没有监听到，导致页面不会显示新的element的值。

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>06_列表渲染</title>
</head>
<body>

<!--
1. 列表显示
  数组: v-for / index
  对象: v-for / key
2. 列表的更新显示
  删除item
  替换item
-->

<div id="demo">
  <h2>测试: v-for 遍历数组</h2>
  <ul>
    <li v-for="(p, index) in persons" :key="index">
      {{index}}--{{p.name}}--{{p.age}}
      --<button @click="deleteP(index)">删除</button>
      --<button @click="updateP(index, {name:'Cat', age: 16})">更新</button>
    </li>
  </ul>
  <button @click="addP({name: 'xfzhang', age: 18})">添加</button>

  <h2>测试: v-for 遍历对象</h2>

  <ul>
    <li v-for="(item, key) in persons[1]" :key="key">{{key}}={{item}}</li>
  </ul>

</div>

<script type="text/javascript" src="../js/vue.js"></script>
<script type="text/javascript">
  new Vue({
    el: '#demo',
    data: {
      persons: [
        {name: 'Tom', age:18},
        {name: 'Jack', age:17},
        {name: 'Bob', age:19},
        {name: 'Mary', age:16}
      ]
    },

    methods: {
      deleteP (index) {
        this.persons.splice(index, 1) // 调用了不是原生数组的splice(), 而是一个变异(重写)方法
              // 1. 调用原生的数组的对应方法
              // 2. 更新界面
      },

      updateP (index, newP) {
        console.log('updateP', index, newP)
        // this.persons[index] = newP  // vue根本就不知道
        this.persons.splice(index, 1, newP)
        // this.persons = []
      },

      addP (newP) {
        this.persons.push(newP)
      }
    }
  })
</script>
</body>
</html>
```

