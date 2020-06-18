# 常用内置指令&自定义指令

### 常用内置指令

1\) v:text : 更新元素的textContent

 2\) v-html : 更新元素的innerHTML

 3\) v-if : 如果为true, 当前标签才会输出到页面

4\) v-else: 如果为false, 当前标签才会输出到页面 

5\) v-show : 通过控制display 样式来控制显示/隐藏 

6\) v-for : 遍历数组/对象

 7\) v-on : 绑定事件监听, 一般简写为@ 

8\) v-bind : 强制绑定解析表达式, 可以省略v-bind

 9\) v-model : 双向数据绑定 

10\) ref : 指定唯一标识, vue 对象通过$els 属性访问这个元素对象 

11\) v-cloak : 防止闪现, 与css 配合: \[v-cloak\] { display: none }

### 自定义指令

```text
1) 注册全局指令
Vue.directive('my-directive', function(el, binding){
    el.innerHTML = binding.value.toupperCase()
})
2) 注册局部指令
directives : {
    'my-directive' : {
        bind (el, binding) {
            el.innerHTML = binding.value.toupperCase()
        }
    }
}
3) 使用指令
v-my-directive='xxx'
```

