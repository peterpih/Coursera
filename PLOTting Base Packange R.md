<div id='table-of-contents'>
###Notes on plotting in R

- [Base Package](#base-plotting-package)
  - [Box Plots](#base-box-plots)
- [ggplot2](#ggplot2-plotting-package) ---\> <a href="http://docs.ggplot2.org/0.9.3.1/index.html" target=_blank>online reference
  + [layering example](#ggplot2-layering-example)
  + [scatterplot example](#ggplot2-scatterplot-example)
  + [scatterplot with error lines example](#ggplot2-scatterplot-with-error-lines-example)
  + [histogram example](#ggplot2-histogram-example)
  + [histogram example](#ggplot2-histogram-example)
  + [pairs example](#ggplot2-pairs-example)
- [Lattice](#lattice-plotting-package)
- [QQ Plot Residuals](#qqplot-residuals)
- [Grouping Graphs](#grouping-graphs)

<div id='base-plotting-package'/>
###Base Plotting 

- **plot**
  - plot(x, y, xlab="xlabel", ylab="ylabel", main="title")
  - plot(fit) - will show 4 graph residual plot
    - plot(resid(fit), ...)
  - plot(dataset) - wil plot an n x n graph of all variables against each other
  - plot(density(resid(fit)), main="Residual Density Graph", xlab="Normally Distributed")  
*(this will give the density graph of the residuals)*
- **lines**
  - lines(x, y)
  - lines(fit)
- **abline**
  - abline(h=, col=, lty=) - horizontal line
  - abline(v=,col=,lty=) - vertical line
  - abline(fit) - fitted line


```{R}
# Example of a scatterplot and regression line:

set.seed(123)                         # for reproducibility
x <- rnorm(20)                        # x variable
y <- rnorm(20)                        # y variable
plot(x,y)                             # shows the points scatter plot
fit <-lm(y~x)                         # fit the points
y_hat <- predict(fit, method="lm")    # predicted y's
lines(x, y_hat, col=1, lty=1)         # plot rergession line
```
<div id='base-box-plots'>
###Examples of Box Plots
- boxplot(data, main="main title", xlab="x label", ylab="y label")
- boxplot(dataset) ie boxplot(mtcars)
- boxplot(y~x, data=dataset) ie boxplot(mpg~wt,data=mtcars)
- boxplot(mtcars$am, mtcars$mpg) ***does not seem to work, different than*** boxplot(mpg~am,data=mtcars)

[TOP](#table-of-contents)

<div id='grouping-graphs'>
###Grouping graphs
- par(mfrow=c(nrows,ncols)) - group graphs together  
*For example, par(nfrom=c(1,2)) gives 1 row of 2 graphs*

[TOP](#table-of-contents)

<div id='ggplot2-plotting-package'/>
### ggplot2

**DO NOT FORGET dev.off() to reset the Base Plot device for ggplot2**

Usually of the form:
- ggplot(data, aes())
  + data
  + aes(x= , y=)
- Type of graph
  + **geom_line**()
  + **geom_histogram**()
- Labels
  + **geom_title**("\<text\>")
  + **xlab**("\<text\>")
  + **ylab**("\<text\>")
- Graphic types
  + **geom_point**(size=, colour=)
  + **geom_line**(aes(linetype=\<grouping\>, size=))
- Other
  + **geom_smooth**()

<div id='ggplot2-scatterplot-example'>
```
# Example of a ggplot2 scatterplot with regression line

g <- ggplot(mtcars, aes(x=hp, y=mpg))   # specify the variables
g <- g + geom_point()                   # graph points
g                                       # show the scatterplot

g <- g + geom_line()                    # connect dots with line
g                                       # show the scatterplot with connecting line

g <- ggplot(mtcars, aes(x=hp, y=mpg))   # specify the variables
g <- g + geom_line()                    # connect dots with line
g                                       # show the scatterplot with connecting line but no points
```
<div id='ggplot2-histogram-example'>
```
# Example of a ggplot2 histogram

g <- ggplot(mtcars, aes(x=hp))          # specify the variables, no y in this case
g <- g + geom_histogram()               # graph histogram
g                                       # show the histogram
```

<div id='ggplot2-layering-example'>
```{R}
# Example of ggplot2 layering

g <- ggplot(data, aes(x-variable, y-variable)
g <- g + geom_point()  # or geom_line()
    + facet_wrap( . ~ type)           # facets for multipanelling
    + labs(x = "x axis label")
    + labs(y = "y axis label")
    + labs(title = "overall title")
    + geom_smooth(method = "lm" )     # smoothing
    + theme_bw(base_family = "...")   # change theme
    
print(g)      # to display the graph

dev.copy(png, file="file name")
dev.off()
```
<div id='ggplot2-scatterplot-with-error-lines-example'>
```{R}
# Example of scatterplot with error lines in ggplot2

g <- ggplot(mtcars, aes(x=hp, y=mpg))
g = g + geom_point(size=4)
g = g + geom_smooth(method=lm)
g
```

<div id='ggplot2-pairs-example'>
```{R}
# Example of plotting pairs in ggplot2

install.packages("GGally")                      # supplementary functions for ggplot2
library(GGally)
ggpairs(swiss, lower=list(continuous="smooth"), params=c(method="loess"))  # nxn plots with regression lines
```
<div id='ggplot2-residuals-example'>
```{R}
# Example of plotting residuals in ggplot2

fit <- lm(x,y)
resid(fit)                  # the residuals
plot(density(resid(fit)))   # is it bell shaped?
qqplot(resid(fit))          # histogram of residuals
qqline(resid(fit))          # line through residuals
```

g <- g + facet_grid(.~variable)

<div id='qqplot-residuals'>
###QQ Plot of regression residuals
```
qqnorm(resid(fit))    # scatterplot of normal distribution
qqline(resid(fit))    # normality regression line
```
[TOP](#table-of-contents)

###Lattice <div id='lattice-plotting-package'>

[TOP](#table-of-contents)
