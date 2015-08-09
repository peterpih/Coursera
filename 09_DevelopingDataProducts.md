
[Shiny](*shiny-section)
[rCharts](*rcharts-section)
[Manipulate](*manipulate-section)

<div id="shiny-section">
###Shiny  
**tutorial:** http://rstudio.github.io/shiny/tutorial  
A **shiny** project is a directory that contains at least two files:
- **server.R**
- **ui.R**

**Installation of shiny**  
http://http://shiny.rstudio.com/tutorial/  
```{R}
require(RTools)
install.packages("shiny")
library(shiny)
```
Example 1:  
```{R}
library(shiny)
runExample("01_hello")  #changes number of bins in a histogram
```

```{R}
library(shiny)
shinyUI(
    pageWithSidebar(
        headerPanel("Data science FTW!"),
        sidebarPanel(
            h3('Sidebar text')
        ),
        mainPanel(
            h3('Main Panel text')
        )
    ) 
)
```
```

<div id="manipulate-section">
###Manipulate  
http://www.rstudio.com/ide/docs/advanced/manipulate  

```{R}
install.packages("manipulate")
library(manipulate)
```
A quick example
```{R}
library(manipulate)
manipulate(plot(1:x), x = slider(1,100))
```
Example from regression class
```{R}
library(manipulate)
myHist <- function(mu){
    hist(Galton$child,col="blue",breaks=100)
    lines(c(mu, mu), c(0, 150),col="red",lwd=5)
    mse <- mean((Galton$child - mu)^2)
    text(63, 150, paste("mu = ", mu))
    text(63, 140, paste("MSE = ", round(mse, 2)))
}
manipulate(myHist(mu), mu = slider(62, 74, step = 0.5))
```
