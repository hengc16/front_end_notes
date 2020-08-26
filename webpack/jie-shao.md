# 介绍

* webpack是当前最流行的前端打包工具
* webpack是用node来实现的，所以可以在module里用node的语法

![](../.gitbook/assets/image%20%2879%29.png)

{% embed url="https://webpack.docschina.org/concepts/" %}

### 安装：

`npm -i webpack`

初始化

`npm init -y`

安装

`npm install webpack webpack-cli --save-dev`

### 打包：

* 开发环境下打包

`./src/index.js -o ./dist/bundle.js --mode=development`

* 生成环境打包

`./src/index.js -o ./dist/bundle.js --mode=production`

\`\`

