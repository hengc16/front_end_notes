# 表单输入绑定\(form input binding\)

常见表单的input type为

1\) text/textarea

2\) checkbox

3\) radio

4\) select 

我们可以通过v-model指令在&lt;input&gt;  &lt;textarea&gt; 以及以上其他元素上创建双向绑定。

通过fill 这个form，点击注册，我希望可以生成我输入的所有信息，以便于以后发送ajax去后台。

![](../.gitbook/assets/image%20%2824%29.png)

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>08_表单输入绑定</title>
</head>
<body>
<!--
1. 使用v-model(双向数据绑定)自动收集数据
  text/textarea
  checkbox
  radio
  select
-->
<div id="demo">
  <form action="/xxx" @submit.prevent="handleSubmit">
    <span>用户名: </span>
    <input type="text" v-model="username"><br>

    <span>密码: </span>
    <input type="password" v-model="pwd"><br>

    <span>性别: </span>
    <input type="radio" id="female" value="女" v-model="sex">
    <label for="female">女</label>
    <input type="radio" id="male" value="男" v-model="sex">
    <label for="male">男</label><br>

    <span>爱好: </span>
    <input type="checkbox" id="basket" value="basket" v-model="likes">
    <label for="basket">篮球</label>
    <input type="checkbox" id="foot" value="foot" v-model="likes">
    <label for="foot">足球</label>
    <input type="checkbox" id="pingpang" value="pingpang" v-model="likes">
    <label for="pingpang">乒乓</label><br>

    <span>城市: </span>
    <select v-model="cityId">
      <option value="">未选择</option>
      <option :value="city.id" v-for="(city, index) in allCitys" :key="city.id">{{city.name}}</option>
    </select><br>
    <span>介绍: </span>
    <textarea rows="10" v-model="info"></textarea><br><br>

    <input type="submit" value="注册">
  </form>
</div>

<script type="text/javascript" src="../js/vue.js"></script>
<script type="text/javascript">
  new Vue({
    el: '#demo',
    data: {
      username: '',
      pwd: '',
      sex: '男',
      likes: ['foot'],
      allCitys: [{id: 1, name: 'BJ'}, {id: 2, name: 'SS'}, {id: 3, name: 'SZ'}],
      cityId: '2',
      info: ''
    },
    methods: {
      handleSubmit () {
        console.log(this.username, this.pwd, this.sex, this.likes, this.cityId, this.info)
        alert('提交注册的ajax请求')
      }
    }
  })
</script>
</body>
</html>
```

