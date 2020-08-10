# 显示动态时间

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';


ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

function Clock(props) {

  return (<div>
    <h1>current time is : {props.date.toLocaleTimeString()} </h1>
  </div>)

}
function run() {
  ReactDOM.render(
    <Clock date = {new Date()}/>,
    document.getElementById('root')
  )
}

setInterval(run,1000);

```



