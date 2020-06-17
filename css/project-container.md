# project-container

use grid to display the project or image galley. 

### set up the grid wrapper to make it responsive

```text
.grid-wrapper{
   display: grid;
   grid-gap: 20px;
   grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
}
```

fill up the screen with one element if the screen is less than 350px; 



