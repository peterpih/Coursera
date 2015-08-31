August 2015: https://class.coursera.org/devdataprod-031  

There are many, many graphics packages to explore, so budget time to download and install. Not all of them install quickly and easily.  

I also strongly recommend you learn how to create GH-pages on github and your-logon.github.io project web site. When I took the class you could prepare and post one of the project deliverables to gh-pages or rpubs.   

Regarding the shiny app, please allocate time during week one to create a shinyio user account and site, create a sample app, post the app, then update the app and post the update. Getting the plumbing to work in this class is critical to success.  

The shinyapp has a timeout provision and a monthly time limit for free use. I found that setting the automatic timeout to five minutes after no activity gave me ample time to test my application and still leave time for the student evaluators to use my application. Some students did not set this limit, and student evaluators could not evaluate the application.   

All in all, this was a fun class and allowed for a lot of creativity to explore a data issue or data set that is personally special to you. If you're a software developer, technical writer, graphics artist or in marketing, I think you'll find the class entertaining and familiar.  


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

```{R}
require(rCharts)
haireye = as.data.frame(HairEyeColor)
n1 <- nPLot(Freq ~ Hair, group='Eye', type='MultiBarChart', data=subset(haireye, sex=='Male'))
n1$save('fig/n1.html', cdn=TRUE)                                    # save as a plot to disk
cat('<iframe src='fig/n1.html', width=100%, height=600></iframe>)   # best way to embed a graph in shiny
```

###Google Vis

http://cran.r-project.org/web/packages/googleVis/googleVis.pdf

Useful links:  
http://cran.r-project.org/web/[ackages/googleVis/vignettes/googleVis.pdf  
https://developers.google.com/chart/interactive/docs/gallery  
https://developers.google.com/chart/interactive/faq  

