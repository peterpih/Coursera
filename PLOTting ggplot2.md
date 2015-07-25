# ggplot2 Commands

Assign the plot to a variable
```{R}
> g <- ggplot(data, aes(x-variable, y-variable)
```

Now add layers
```{R}
> g + geom_point()  # or geom_line()
    + facet_wrap( . ~ type)           # facets for multipanelling
    + labs(x = "x axis label")
    + labs(y = "y axis label")
    + labs(title = "overall title")
    + geom_smooth(method = "lm" )     # smoothing
    + theme_bw(base_family = "...")   # change theme
    
> print(g)      # to display the graph

> dev.copy(png, file="file name")
> dev.off()
```
###Scatterplot with line and errors
```{R}
g <- ggplot(mtcars, aes(y=y, x=x))
g = g + ggeom_point(size=4)
g = g + geom_smooth(method=lm)
g
```
###Plotting Swiss Data
```{R}
install.packages("GGally")
library(GGally)
library(ggplot2)
ggpairs(swiss, lower=list(continuous="smooth"), params=c(method="loess"))
```
###Plotting Residuals
```{R}
fit <- lm(x,y)
resid(fit)                  # the residuals
plot(density(resid(fit)))   # is it bell shaped?
qqplot(resid(fit))          # histogram of residuals
qqline(resid(fit))          # line through residuals
```
