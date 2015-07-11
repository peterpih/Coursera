###Notes on plotting in R

###Base Plotting
```
**plot**(x,y)
**lines**(x, y)
**xlab**()
**ylab**()
**abline**(h=, col=, lty=)
**abline**(v=,col=,lty=)
```
```
set.seed(123)
x <- rnorm(20)
y <- rnorm(20)
plot(x,y)   # shows the points
fit <-lm(y~x)
y_hat <- predict(fit, method="lm")
lines(x, y_hat, col=1, lty=1)
```

### DO NOT FORGET dev.off() to reset the Base Plot device

###ggplot
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
