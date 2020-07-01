# 收集表单数据（form）

做一个username password 的login

**创建一个loginForm的静态组件**

```jsx
    class LoginForm extends React.Component{
        render(){
            return(
                <form action="">
                    username <input type="text"/>
                    password <input />
                    <input type="submit" value = "login"/>
                </form>
            )
        }
    }
  
  ReactDOM.render(<LoginForm />, document.getElementById('example'))
```

点击login， alert用户值

**用2种不同的方法去收集表单的数据。**

**受控组件**：表单输入数据能自动收集成状态， onChange\(\)

**非受控组件**： 需要时才手动读取表单输入框中的数据 ref

```jsx
<script type="text/babel">
  /*
  1. 问题: 在react应用中, 如何收集表单输入数据
  2. 包含表单的组件分类
    受控组件
    非受控组件
  */
  /*
  需求: 自定义包含表单的组件
    1. 界面如下所示
    2. 输入用户名密码后, 点击登陆提示输入信息
    3. 不提交表单
  */
    class LoginForm extends React.Component{
        constructor(props){
            super(props)
            this.state = {
                pwd : ''
            }
            this.handleSubmit = this.handleSubmit.bind(this)
            this.handleChange = this.handleChange.bind(this)
        }
        handleSubmit(event){
            const name = this.nameInput.value
            const pwd = this.state.pwd
            alert(`username is ${name}, password is ${pwd}`)
            //阻止默认行为， 阻止提交
            event.preventDefault();
            
        }
        handleChange(event){
            //1. 读取输入的值
            const pwd = event.target.value
            //更新pwd 状态
            this.setState({pwd})
        }
        render(){
            return(
                <form action="" onSubmit = {this.handleSubmit}>
                    username <input type="text" ref = {input => this.nameInput = input}/>
                    password <input type ="password" value = {this.state.pwd} onChange = {this.handleChange}/>
                    <input type="submit" value = "login"/>
                </form>
            )
        }
    }
  
  ReactDOM.render(<LoginForm />, document.getElementById('example'))
</script>
```

这里password是以受控组件形式实现收集数据的

username是以非受控形式实现收集数据的。

