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

    dev.copy(png, file="file name")
    dev.off()
```

