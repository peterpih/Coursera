<div id='table-of-contents'>
###Notes on plotting in R

- [Base Package](#base-plotting-package)
  - [Box Plots](#base-box-plots)
- [ggplot2](#ggplot2-plotting-package) <a href="http://docs.ggplot2.org/0.9.3.1/index.html" target=_blank>useful link
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
-   
```
# Example of scatterplot with regression line

g <- ggplot(mtcars, aes(x=hp, y=mpg))   # specify the variables
g <- g + geom_point()                   # graph points
g                                       # show the scatterplot

g <- g + geom_line()                    # connect dots with line
g                                       # show the scatterplot with connecting line

g <- ggplot(mtcars, aes(x=hp, y=mpg))   # specify the variables
g <- g + geom_line()                    # connect dots with line
g                                       # show the scatterplot with connecting line but no points
```
```
# Example of a histogram

g <- ggplot(mtcars, aes(x=hp))          # specify the variables, no y in this case
g <- g + geom_histogram()               # graph histogram
g                                       # show the histogram
```

g <- g + geom_histogram(colour="black", bin=20)
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
