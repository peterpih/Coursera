
[Manipulate](*manipulate-section)


<div id="manipulate-section">
###Manipulate  
http://www.rstudio.com/ide/docs/advanced/manipulate  

```{R}
install.packages("manipulate")
library(manipulate)
```
```{R}
library(manipulate)
manipulate(plot(1:x), x = slider(1,100))
```
