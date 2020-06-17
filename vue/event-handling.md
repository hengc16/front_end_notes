# event handling

handle on click event 

```markup
<button v-on:click="goToStudentLink">Register Now</button>
```

单写一个method去handle goToStudentLink这个event。 

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
     },
      methods: {
      
            goToStudentLink: function()
           {            
             alert('You will be redirected to Student Link.')       
             window.location.href = 'https://www.bu.edu/studentlink'      
            } 
     }
 })
      
```





