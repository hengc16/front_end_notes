# babel



babel用途时convert es6以后的js文件 to browerse可以兼容的老的版本。



set up

```markup
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
 <title>Test</title>
 <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/6.21.1/babel.min.js"></script>
 <link rel="stylesheet" href="index.css">
</head>
<body>
 <div id="root"></div>
 <script type="text/babel">
   // ES6 / React / JSX code from here
 </script>
</body>
</html>
```

