###Quiz 1

**Question 1.1**  
Consider the following code for the cars data set  
```
library(manipulate)
myPlot <- function(s) {
    plot(cars$dist - mean(cars$dist), cars$speed - mean(cars$speed))
    abline(0, s)
}
```
This function plots distance versus speed, each de-meaned and an associated line of slope s. Which of the following code will make a manipulate plot that creates a slider for the slope?  

**Answer 1.1**  
`manipulate(myPlot(s), s = slider(0, 2, step = 0.1))`

**Question 1.2**  
Which of the following code uses the rCharts package to create a sortable and searchable data table for the airquality data set? Assume the rCharts package and the airquality data set have already been loaded into R.  

**Answer 1.2**  
` dTable(airquality, sPaginationType = "full_numbers")`

**Question 1.3**  
A basic shiny data product requires:  

**Answer 1.3**  
A ui.R and server.R file or a A server.R file and a directory called www containing the relevant html   

**Question 1.4**  
What is incorrect about the followig syntax in ui.R?  
```
library(shiny)
shinyUI(pageWithSidebar(
  headerPanel("Data science FTW!"),
  sidebarPanel(
    h2('Big text')
    h3('Sidebar')
  ),
  mainPanel(
      h3('Main Panel text')
  )
))
```
**Answer 1.4**  
`Missing a comma in the sidebar panel`  

**Question 1.5**  
Consider the following code in ui.R  
```
shinyUI(pageWithSidebar(
  headerPanel("Example plot"),
  sidebarPanel(
    sliderInput('mu', 'Guess at the mu',value = 70, min = 60, max = 80, step = 0.05,)
  ),
  mainPanel(
    plotOutput('newHist')
  )
))
```

And the following server.R code.  
```
library(UsingR)
data(galton)

shinyServer(
  function(input, output) {
    output$myHist <- renderPlot({
      hist(galton$child, xlab='child height', col='lightblue',main='Histogram')
      mu <- input$mu
      lines(c(mu, mu), c(0, 200),col="red",lwd=5)
      mse <- mean((galton$child - mu)^2)
      text(63, 150, paste("mu = ", mu))
      text(63, 140, paste("MSE = ", round(mse, 2)))
      })
    
  }
)
```
Why isn't it doing what we want?  

**Answer 1.5**  
`The server.R output name isn't the same as the plotOutput command used in ui.R.`  

###Quiz 2  
**Question 2.1**  
In the slidify YAML text. Changing the framework from io2012 to shower does what?  
**Answer 2.1**  
It changes the html5 framework thus changing the style of the slides.  

**Question 2.2**  
You wrote R code in a slidify document as follows  

```{r}
fit <- lm(y ~ x1 + x2 + x3)
summary(fit)
```

If you want to hide the results of the summary statement (yet still have it run) what should you do?  
**Answer 2.2**
Add a results = 'hide' option in the {r} call of the code chunk  

**Question 2.3**  
You wrote R code in a slidify document as follows  
```{R}
fit <- lm(y ~ x1 + x2 + x3)
summary(fit)
```
If you want to display the results, but not the actual code, what should you do?  
**Answer 2.3**  
Add a echo = FALSE option in the {r} call of the code chunk  

**Question 2.4**  
R studio presentation tool does what?  
**Answer 2.4**  
Creates HTML5 slides using a generalized markdown format having an extention Rpres and creates reproducible presentations by embedding and running the R code from within the presentation document.  

**Question 2.5**  
In Rstudio presenter, if you do not want the code to be evaluated, what option do you need to add to the {r} options?  
**Answer 2.5**  
eval = FALSE  

**Question 2.6**  
When presenting data analysis to a broad audience, which of the following should be done?  
**Answer 2.6**  
Summarize the problem first.  

###Quiz 3
**Question 3.1**  
Which of the following items is required for an R package to pass R CMD check without any warnings or errors?  
**Answer 3.1**  
DESCRIPTION file  

**Question 3.2**  
Which of the following is a generic function in a fresh installation of R, with only the default packages loaded?  
**Answer 3.2**  
predict  

**Question 3.3**  
What function is used to obtain the function body for an S4 method function?  
**Answer 3.3**  
getMethod()  

**Question 3.4**  
Which one of the following functions must be defined in order to deploy an R function on yhat?  
**Answer 3.4**  
model.predict  

**Question 3.5**  
Please download the R package DDPQuiz3 from the course web site. Examine the createmean function implemented in the R/ sub-directory. What is the appropriate text to place above the createmean function for Roxygen2 to create a complete help file?  
**Answer 3.5**  
```
#' This function calculates the mean
#' 
#' @param x is a numeric vector
#' @return the mean of x
#' @export
#' @examples 
#' x <- 1:10
#' createmean(x)
```


