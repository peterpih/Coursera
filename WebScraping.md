# Web Scraping (under construction)

This example is from http:  
http://giventhedata.blogspot.co.uk/2012/08/r-and-web-for-beginners-part-iii.html

German Portfolio:  
http://www.boerse-frankfurt.de/en/portfolio/view?depot_id=1665120

Get prices From Yahoo:  
http://stackoverflow.com/questions/6299220/access-a-url-and-read-data-with-r

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
###From Machine Learning Course
```{R}
require("quantmod")
library(quantmod)
from.dat <- as.Date("01/01/12", format="%m/%d/%y")
to.dat <- as.Date("12/31/14", format="%m/%d/%y")
getSymbols("GOOG", src="google", from = from.dat, to = to.dat)
```

**For getting last 10 days of data**
```{R}
require(lubridate)
from.dat <- as.Date(today()-10, format="%m/%d/%y")
to.dat <- as.Date(today(), format="%m/%d/%y")
quoteList <- c("GOOG", "GS", "AAPL")
getSymbols("GOOG", src="yahoo", from = from.dat, to = to.dat)
getQuote(quoteList)
```

```{R}
mGoog <- to.monthly(GOOG)
googOpen <- Op(mGoog)
ts1 <- ts(googOpen,frequency=12)
plot(ts1,xlab="Years+1", ylab="GOOG")
```
**Time Series Decomposition**
```{R}
plot(decompose(ts1),xlab="Years+1")
```
