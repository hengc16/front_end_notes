# 过渡&动画

### 概况

Vue 在插入、更新或者移除 DOM 时，提供多种不同方式的应用过渡效果。包括以下工具：

* 在 CSS 过渡和动画中自动应用 class
* 可以配合使用第三方 CSS 动画库，如 Animate.css
* 在过渡钩子函数中使用 JavaScript 直接操作 DOM
* 可以配合使用第三方 JavaScript 动画库，如 Velocity.js

### 过渡类名

![](../.gitbook/assets/image%20%2819%29.png)

 `v-enter-active` 和 `v-leave-active` 可以控制进入/离开过渡的不同的缓和曲线

click toggle render, hello会fade away

![](../.gitbook/assets/image%20%2832%29.png)

```jsx
<div id="example-1">
  <button @click="show = !show"> // click 开关
    Toggle render
  </button>
  <transition name="slide-fade">  //transition标签
    <p v-if="show">hello</p>
  </transition>
</div>
new Vue({
  el: '#example-1',
  data: {
    show: true
  }
})
/* 可以设置不同的进入和离开动画 */
/* 设置持续时间和动画函数 */
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active for below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
```

### 动画

```jsx
<div id="example-2">
  <button @click="show = !show">Toggle show</button>
  <transition name="bounce">
    <p v-if="show">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris facilisis enim libero, at lacinia diam fermentum id. Pellentesque habitant morbi tristique senectus et netus.</p>
  </transition>
</div>

new Vue({
  el: '#example-2',
  data: {
    show: true
  }
})
.bounce-enter-active {
  animation: bounce-in .5s;
}
.bounce-leave-active {
  animation: bounce-in .5s reverse;
}
@keyframes bounce-in {
  0% {  //可以理解为时间的0%时 做的事
    transform: scale(0);
  }
  50% {  //时间过一半的时候  scale字的size 1。5
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
```



