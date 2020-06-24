# class 和style绑定\(class and style binding\)

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>04_class与style绑定</title>
  <style>
    .classA {
      color: red;
    }
    .classB {
      background: blue;
    }
    .classC {
      font-size: 20px;
    }
  </style>
</head>
<body>

<!--
1. 理解
  在应用界面中, 某个(些)元素的样式是变化的
  class/style绑定就是专门用来实现动态样式效果的技术
2. class绑定: :class='xxx'
  xxx是字符串
  xxx是对象
  xxx是数组
3. style绑定
  :style="{ color: activeColor, fontSize: fontSize + 'px' }"
  其中activeColor/fontSize是data属性
-->

<div id="demo">
  <h2>1. class绑定: :class='xxx'</h2>
  <p :class="myClass">xxx是字符串</p>
  <p :class="{classA: hasClassA, classB: hasClassB}">xxx是对象</p>
  <p :class="['classA', 'classB']">xxx是数组</p>

  <h2>2. style绑定</h2>
  <p :style="{color:activeColor, fontSize}">:style="{ color: activeColor, fontSize: fontSize + 'px' }"</p>

  <button @click="update">更新</button>

</div>

<script type="text/javascript" src="../js/vue.js"></script>
<script type="text/javascript">
  new Vue({
    el: '#demo',
    data: {
      myClass: 'classA',
      hasClassA: true,
      hasClassB: false,
      activeColor: 'red',
      fontSize: '20px'
    },

    methods: {
      update () {
        this.myClass = 'classB'
        this.hasClassA = !this.hasClassA
        this.hasClassB = !this.hasClassB
        this.activeColor = 'yellow'
        this.fontSize = '30px'
      }
    }
  })
</script>
</body>
</html>
```
