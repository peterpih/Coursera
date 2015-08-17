```{R}
install.packacges("dplyr")
library(dplyr)

mydf <- read.csv(file, stringsAsFactors=FALSE)
cran <- tbl_df(mydf)
cran                            # better table printing
```
