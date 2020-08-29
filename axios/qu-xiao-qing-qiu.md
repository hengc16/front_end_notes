# 取消请求



### Cancellation

You can cancel a request using a _cancel token_.

> The axios cancel token API is based on the withdrawn [cancelable promises proposal](https://github.com/tc39/proposal-cancelable-promises).

You can create a cancel token using the `CancelToken.source` factory as shown below:

```javascript
const CancelToken = axios.CancelToken;
const source = CancelToken.source();

axios.get('/user/12345', {
  cancelToken: source.token
}).catch(function (thrown) {
  if (axios.isCancel(thrown)) {
    console.log('Request canceled', thrown.message);
  } else {
    // handle error
  }
});

axios.post('/user/12345', {
  name: 'new name'
}, {
  cancelToken: source.token
})

// cancel the request (the message parameter is optional)
source.cancel('Operation canceled by the user.');
```

You can also create a cancel token by passing an executor function to the `CancelToken` constructor:

```javascript
const CancelToken = axios.CancelToken;
let cancel;

axios.get('/user/12345', {
  cancelToken: new CancelToken(function executor(c) {
    // An executor function receives a cancel function as a parameter
    cancel = c;
  })
});

// cancel the request
cancel();
```

这里我们主要用第2种方法：

![](../.gitbook/assets/image%20%28112%29.png)

对于上面发请求，我们可以在config里去配置cancelToken来对一个global variable赋予它cancel函数的回调功能。

在拿到请求或取消成功，都把cancel清空。

![](../.gitbook/assets/image%20%28115%29.png)

这里可以通过调用cancel来取消响应的。 如果请求还没发送时，concel函数为空，一但发送了请求， cancel将被赋值为函数形式，这时候就可以调用它来取消请求。

