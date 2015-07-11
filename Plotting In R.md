###Notes on plotting in R

###Base Plotting
```
plot(x,y)
xlab()
ylab()
abline()
```

###ggplot

```
g <- ggplot(\<data\>, aes(x=\<x var\>, y=\<y var\>), fill=variable)
g <- g + geom.histogram(colour="black", bin=20)
g <- g + facet_grid(.~variable)

# then show the graph
g
```
