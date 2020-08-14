# Vue组件 父到子

### 父子组件的通讯：

* 父组件给子组件静态传值。

```jsx
这里是父组件  直接在tag 里加要传的值
  <div class="hello">
    <Counter num = '10'></Counter>
  </div>
  
```

```jsx
这是子组件， 通过props 来接收， 注意是'num' 要保持一致
<script>
    export default {
        props:['num'],
        data() {
            return {
                num: 0,
                msg: 'hello vue'
            }
        }
```

如果是动态值

```jsx
  父组件
  <div class="hello">
    <Counter v-bind:num = "num"></Counter>
    <p>parent: {{num}}</p>
  </div>
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
      }
  }
</script>
```

![](../.gitbook/assets/image%20%2862%29.png)

这里我们点击+ - button  parent值不会变， 可以看出这是父到子单向流通的。

### 

