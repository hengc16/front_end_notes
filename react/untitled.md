# 组件的三大属性：props

### 理解：

每个组件instance都会有props这个属性

而props里存的是这个组件所需要的组件标签

### 需求:

实现一个组件可以显示一个员工信息的组件。

| 姓名 | 不能为空 |
| :--- | :--- |
| 性别 | 默认：男 |
| 年龄 | 默认：18 |

 人员组件给它加props。 也就是属性。

### 操作：

* **读取某个属性值：**
  * this.props.propertyName
* **对props中的属性值进行类型限制等，（这里引用了prop-types这个库）**
  * Person.propTypes = { name: PropTypes.string} 规定name属性为string类型。
* **默认属性：**
  * 也就是person的default 值。
  * Person.defaultProps = { name: 'bob'}
* 扩展运算符{...el1} 
  * 可以用在打包：
    * function fn\(...input\) {} , 调用fn\(1,2,3\)  ...会自动将input转换为array
  * 也可以用在解析：
    * array1 = \[1,2,3\]    array2 = \[0, ...array1, 4, 5, 6\] 
    * 打印array2  则为  0 1 2 3 4 5 6

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

</head>
<body>
    <div id ="container1"></div>
    <div id ="container2"></div>


<script src="../js_link/react.development.js"></script>
<script src="../js_link/react-dom.development.js"></script>
<script src="../js_link/babel.min.js"></script>
<script src="../js_link/prop-types.js"></script>
<script type="text/babel">
    //1.定义组件
    //a.工厂函数组件。
    
    function MyComponent(props){
        return (
            <ul>
                <li>name : {props.name}</li>
                <li>age: {props.age}</li>
                <li>sex: {props.sex}</li>
            </ul>
        )
    }
    //组件标签
    const p1 = {
        name : 'Jay',
        age : 21,
        sex : 'male'
    }
    const p2 = {
        name : 'Tina',
        age : 19,
        sex : 'female'
    }
    //组件属性默认值
    MyComponent.defaultProps = {
        sex: 'male',
        age: 18
    }
    //组件属性检查
    MyComponent.prototype = {
        name : PropTypes.string.isRequired,
        age : PropTypes.number,

    }
    //b. ES6类组件
    class MyComponent2 extends React.Component{
        render(){
            //注意这样要用this. 来调用props的标签属性
            return (
            <ul>
                <li>name:{this.props.name}</li>
                <li>age: {this.props.age}</li>
                <li>sex: {this.props.sex}</li>
            </ul>
        )
        }
    }
    //2. 渲染组件
    ReactDOM.render(<MyComponent {...p1}/>, document.getElementById('container1'));
    ReactDOM.render(<MyComponent2 {...p2}/>, document.getElementById('container2'));
</script>
</body>
</html>
```



