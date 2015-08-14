
USing html directly: http://shiny.rstudio.com/articles/html-ui.html  
Debugging: http://shiny.rstudio.com/articlas/debugging.html  



[Shiny](*shiny-section)  
[rCharts](*rcharts-section)  
[Manipulate](*manipulate-section)  
[rCharts](*rcharts-section)

<div id="shiny-section">
###Shiny  
**tutorial:** http://rstudio.github.io/shiny/tutorial  
**tutorial:** http://http://shiny.rstudio.com/tutorial/  
A **shiny** project is a directory that contains at least two files:
- **server.R**
- **ui.R**

**Installation of shiny**  
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

<div id="manipulate-section">
###Manipulate  
Documenatation: http://www.rstudio.com/ide/docs/advanced/manipulate  

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

**Render** vs **Reactive** statements (More Shiny video)


```
$ runApp(display='showcase')
```

<div id='rcharts-section'>
###rCharts
Documentation: http://ramnathv.gothub.io/rCharts/  
Install rCharts from github  
'''{R}
require(rCharts)
haireye = as.data.frame(HairEyeColor)
n1 <- nPLot(Freq ~ Hair, group='Eye', type='MultiBarChart', data=subset(haireye, sex=='Male'))
n1$save('fig/n1.html', cdn=TRUE)                                    # save as a plot to disk
cat('<iframe src='fig/n1.html', width=100%, height=600></iframe>)   # best way to embed a graph in shiny
```


