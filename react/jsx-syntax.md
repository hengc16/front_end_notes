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
