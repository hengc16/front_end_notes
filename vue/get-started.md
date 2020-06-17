# get started



To include Vue, we add the following to the bottom of the _index.html_ file:

```markup
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

our html file will look like this:

```markup
<--index.html-->
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Sample Vue Application</title>
    </head>
    <body>
        <div id="app">
            <h1>Course Name</h1>
        </div>
        
        <!--Include Vue-->
        <script src="https://cdn.jsdelivr.net/npm/vue"></script>
    </body>
</html>
```

in order to use Vue, we need to new a vue object.

```javascript
            var app = new Vue({
                el: '#app',
                data: {
                    courseName: 'CS601: Web Application Development'
                }
            })

```

as you can see the el: \#app is linked to our div which id = "app"  in order to change the date of this div. we need to use {{}} to receive data from vue.

```markup
<div id="app">
    <h1>{{ courseName }}</h1>
</div>
```

the h1 will change from course name to CS601: Web Application Development.

![](../.gitbook/assets/image%20%284%29.png)

Vue is reactive, whenever you change your data in js, your browser will show the relative change immediately. 

