# JSX syntax

### JavaScript 表达式

```jsx
ReactDOM.render(
    <div>
      <h1>{1+1}</h1>
    </div>
    ,
    document.getElementById('example')
);
```

### 注意：

*  在 JSX 中不能使用 **if else** 语句，但可以使用 **conditional \(三元运算\)** 表达式来替代。以下实例中如果变量 **i** 等于 **1** 浏览器将输出 **true**, 如果修改 i 的值，则会输出 **false**.

### 样式

```jsx
var myStyle = {
    fontSize: 100,
    color: '#FF0000'
};
ReactDOM.render(
    <h1 style = {myStyle}>菜鸟教程</h1>,
    document.getElementById('example')
);
```

```jsx
let classNameList = ['redbg', 'strong'].join(" ");
let element = (
    <div>
        <h1 className = {classNameList} >hello world</h1>
    </div>
)
//注意jsx里给tag加class 需要使用className
//如果一个tag有多个class name， 可以使用数组.join 空格来加入
```

### 注释

```jsx
ReactDOM.render(
    <div>
    <h1>菜鸟教程</h1>
    {/*注释...*/}
     </div>,
    document.getElementById('example')
);
```

### 数组

```jsx
var arr = [
  <h1>菜鸟教程</h1>,
  <h2>学的不仅是技术，更是梦想！</h2>,
];
ReactDOM.render(
  <div>{arr}</div>,
  document.getElementById('example')
);
```

### jsx 语法规则

* 定义虚拟dom时，不要用引号
* 标签中混入js表达式时用{}
* jsx里样式的类名指定不要用class， 要用className
* 内联样式要用style = {{key:value}} 的形式去写
  * &lt;span style = {{color: 'white', fontSize: '29'}} &gt;&lt;/span&gt;
* 虚拟dom必须只有一个根标签
* 标签必须闭合
* 标签首字母
  * 小写字母开头，则将该标签转为html中同名元素，若html中无该标签对应的元素，则报错。
  * 若大写字母开头，reat就会去渲染对应的组件，如果组件不存在，则报错。

