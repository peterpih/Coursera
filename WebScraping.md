# Web Scraping (under construction)

This example is from http:  
//giventhedata.blogspot.co.uk/2012/08/r-and-web-for-beginners-part-iii.html

German Portfolio:  
http://www.boerse-frankfurt.de/en/portfolio/view?depot_id=1665120


from inside RStudio:
```{R}
> library(XML)
> library(swirl)
```

### I've tried to use on Dax real time prices
```{R}
> url <- "http://www.boerse-frankfurt.de/en/equities/realtime+quotes#tab_id=dax&reiter=dax"
> dax.doc <- htmlParse(url)
> dax.tabs <- readHTMLTable(dax.doc)
```
