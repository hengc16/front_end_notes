# Directives and attribute binding

use v-bind directive to an a tag to bind a link to a href.

```text
<a v-bind:href="link">View Course Details</a>    
```

in the main js . we add the link to our vue data. 

```javascript
var app = new Vue({
    el: '#app',
    data: {
        courseName: 'CS601: Web Application Development',
        link: 'http://www.bu.edu/csmet/academic-programs/courses/cs601/'
    }
})
```

### attribute binding: 

bind &lt;img&gt; element's src attribute to our vue instance. 

```markup
<img :src="logoSrc" alt="Boston University Logo" />
```

```javascript
var app = new Vue({
    el: '#app',
    data: {
        courseName: 'CS601: Web Application Development',
        link: 'http://www.bu.edu/csmet/academic-programs/courses/cs601/',
        logoSrc: './images/bu-logo.gif'
    }
})
```

