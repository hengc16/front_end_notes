# Grid

![](../.gitbook/assets/image%20%2810%29.png)

## container：

### columns

grid-template-columns: 300px, 300px,300px.  3列300px each。

fr 更responsive 

grid-template-columns: 1fr, 1fr, 2fr. 

![](../.gitbook/assets/image%20%285%29.png)

### rows

grid-template-rows: 

### auto-fill + minmax

通过对column进行auto-fill+ minmax 来实现responsive。

grid-template-columns: repeat\(auto-fill, minmax\(200px, 1fr\)\);

这里如果element小于200，就会直接变成当前界面能发下的最大值。

## individual item

grid-column: 1/-1;   will take up the rest space. 

