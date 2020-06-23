# 实现动态展示列表数据

### 功能：动态展示列表数据。

难点： 如何将一个数组的每个element 插入到ul 对应的每个li里。

用array.map方法来对每个element 做处理。

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

</head>
<body>
    <div id ="list"></div>


<script src="../js_link/react.development.js"></script>
<script src="../js_link/react-dom.development.js"></script>
<script src="../js_link/babel.min.js"></script>
<script type="text/babel">
    //data
    const data_array = ["cat1",
                        "cat2",
                        "cat3",
                        "cat4"
                        ];
    //创建虚拟DOM
    const vDom = <ul>
                {
                    data_array.map((name,index) =>
                     <li key={index}> 
                     {name}
                     </li>)
                }
                </ul>;
    //渲染虚拟DOM
    ReactDOM.render(vDom, document.getElementById("list"))

</script>
</body>
</html>
```

![](../.gitbook/assets/image%20%2836%29.png)

