# 子组件传父组件

在vue里数据是单向流通的，如果想让子组件传值给父组件需要通过$emit\(\) 来实现

### 父组件

```jsx
<template>
  <div class="hello">
    <Counter v-bind:num = "num" v-on:incre = "increment" v-on:decre = "decrement"></Counter>
    <p>parent: {{num}}</p>
  </div>
</template>

<script>
import Counter from './counter'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      num: 10,
    }
  },
  components : {
    Counter
  },
  methods: {
    increment(){
      this.num++;
    },
    decrement(){
      this.num--;
    }
  }
}
</script>
```

注意 这里的v-on: incre 的method name 是自己定义的， 一会在子组件的$emit\(\)里要用到

### 子组件

```jsx
<template>
    <div>
        <button @click = 'increment'>+</button>
        <button v-on:click ='decrement'>-</button>
        <p><span>{{num}}</span></p>
    </div>
</template>
<script>
    export default {
        props:['num'],
        data() {
            return {
                num: 0,
                msg: 'hello vue'
            }
        },
        methods : {
            increment(){
                this.$emit('incre');
            },
            decrement(){
                this.$emit('decre');
            }
        }
    }
</script>
```

通过$emit\(\) 来调用父组件的method，从而实现子传父

![](../.gitbook/assets/image%20%2863%29.png)

实现了双向同步。

