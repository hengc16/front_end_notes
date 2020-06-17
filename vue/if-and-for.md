# if and for

**in vue, we use v-if to do particular condition.** 

```markup
        <div id="app">
            <img :src="logoSrc" alt="Boston University Logo" />
            
            <h1>Course Name</h1>
            
            <!--Bind link property from Vue instance-->
            <a v-bind:href="link">View Course Details</a>
            <p v-if="offeredOnline">Offered on campus and online</p>

            <p v-else>Offered on campus only</p>
        </div>
```

in var instance. 

```javascript
            var app = new Vue({
                el: '#app',
                data: {
                    courseName: 'CS601: Web Application Development',
                    link: 'http://www.bu.edu/csmet/academic-programs/courses/cs601/',
                    logoSrc: './images/bu-logo.gif'
                    offeredOnline: true
                }
            })
```

use v-for to perform looping in vue. 

```markup
<ul>
    <li v-for="prerequisite in prerequisites">{{ prerequisite }}</li>
</ul>
```

```javascript
            var app = new Vue({
                el: '#app',
                data: {
                    courseName: 'CS601: Web Application Development',
                    link: 'http://www.bu.edu/csmet/academic-programs/courses/cs601/',
                    logoSrc: './images/bu-logo.gif'
                    offeredOnline: true,
                    offeredBlended: true,
                    prerequisites: [
                        'CS200',
                        'CS231',
                        'CS232',
                        'CS300'
                    ]
                }
            })
```

![](../.gitbook/assets/image%20%282%29.png)

