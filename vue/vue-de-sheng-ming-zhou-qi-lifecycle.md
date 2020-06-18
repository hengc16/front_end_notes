# Vue的生命周期（lifeCycle）

Vue的生命周期，为Vue实例从创建到销毁中间所发生的event。 主要分为3个大的阶段，initialization，update（re-rending），destruction（destroy\). 每个阶段都会对应生命周期的callback function，这些生命周期回调函数也叫钩子。



### beforeCreated到Created生命周期

![](../.gitbook/assets/image%20%2821%29.png)

### Created到beforeMount： 

这里将template或目标的el的outerHTML作为模板存入内存，在内存进行解析，以便以后批量渲染。

![](../.gitbook/assets/image%20%2824%29.png)

### beforeMount 到mounted

![](../.gitbook/assets/image%20%2815%29.png)

### mounted到beforeDestroy：更新



![](../.gitbook/assets/image%20%2825%29.png)

### beforeDestroy到destroyed

![](../.gitbook/assets/image%20%2826%29.png)



### 例子

now you see me ! 会每秒闪动一次。 我们需要在初始化显示之后立刻调用setInterval 函数， 在beforeDestroy时调用clearInterval 来收尾。destory vue按键来销毁触发$destroy\(\). 

![](../.gitbook/assets/image%20%2814%29.png)

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>09_Vue实例_生命周期</title>
</head>
<body>
<!--
1. vue对象的生命周期
  1). 初始化显示
    * beforeCreate()
    * created()
    * beforeMount()
    * mounted()
  2). 更新状态
    * beforeUpdate()
    * updated()
  3). 销毁vue实例: vm.$destory()
    * beforeDestroy()
    * destoryed()
2. 常用的生命周期方法
  created()/mounted(): 发送ajax请求, 启动定时器等异步任务
  beforeDestroy(): 做收尾工作, 如: 清除定时器
-->

<div id="test">
  <button @click="destroyVue">destroy vue</button>
  <p v-if="isShow">now you see me! </p>
</div>

<script type="text/javascript" src="../js/vue.js"></script>
<script type="text/javascript">
  new Vue({
    el: '#test',
    data: {
      isShow: true
    },

    mounted () {
      // 执行异步任务
      this.intervalId = setInterval(() => {
        console.log('-----')
        this.isShow = !this.isShow
      }, 1000)
    },

    beforeDestroy() {
      console.log('beforeDestroy()')
      // 执行收尾的工作
      clearInterval(this.intervalId)
    },

    methods: {
      destroyVue () {
        this.$destroy()
      }
    }
  })


</script>
</body>
</html>
```

