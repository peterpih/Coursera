<div id='table-of-contents'>
###Notes on plotting in R

- [Base Package](#base-plotting-package)
- [ggplot2](#ggplot2-plotting-package)
- [Lattice](#lattice-plotting-package)
- [Grouping Graphs](#grouping-graphs)

<div id='base-plotting-package'/>
###Base Plotting 

- **plot**
  - plot(x,y)
  - plot(fit) - will show 4 graph residual plot
    - plot(resid(fit))
  - plot(dataset) - wil plot an n x n graph of all veriables against each other
  - plot(density(resid(fit)), main="Residual Density Graph", xlab="Normally Distributed")  
*(this will give the density graph of the residuals)*
- **lines**
  - lines(x, y)
  - lines(fit)
- **xlab**("label text")
- **ylab**("label text")
- **abline**
  - abline(h=, col=, lty=) - horizontal line
  - abline(v=,col=,lty=) - vertical line
  - abline(fit) - fitted line

Example of a scatterplot and regression line:
```{R}
set.seed(123)                         # for reproducibility
x <- rnorm(20)                        # x variable
y <- rnorm(20)                        # y variable
plot(x,y)                             # shows the points scatter plot
fit <-lm(y~x)                         # fit the points
y_hat <- predict(fit, method="lm")    # predicted y's
lines(x, y_hat, col=1, lty=1)         # plot rergession line
```
```
boxplot(<data>, main="main title", xlab="x label", ylab="y label")
```
[TOP](#table-of-contents)

<div id='grouping-graphs'>
###Grouping graphs
- par(mfrow=c(nrows,ncols)) - group graphs together  
For example, par(nfrom=c(1,2)) gives 1 row of 2 graphs

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
- Indicator
  + **geom_point**(size=, colour=)
  + **geom_line**(aes(linetype=\<grouping\>, size=))
- Other
-   + **geom_smooth**()
-   
```
g <- ggplot(\<data\>, aes(x=\<x var\>, y=\<y var\>), fill=variable)
g <- g + geom.histogram(colour="black", bin=20)
g <- g + facet_grid(.~variable)

# then show the graph
g
```
[TOP](#table-of-contents)

###Lattice <div id='lattice-plotting-package'>

[TOP](#table-of-contents)
