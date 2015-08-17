```{R}
install.packacges("dplyr")
library(dplyr)

mydf <- read.csv(file, stringsAsFactors=FALSE)
cran <- tbl_df(mydf)
cran                            # better table printing
```
| First, we are shown the class and dimensions of the dataset. Just below that, we get a preview of the data. Instead of  
| attempting to print the entire dataset, dplyr just shows us the first 10 rows of data and only as many columns as fit  
| neatly in our console. At the bottom, we see the names and classes for any variables that didn't fit on our screen.  

| According to the "Introduction to dplyr" vignette written by the package authors, "The dplyr philosophy is to have small  
| functions that each do one thing well." Specifically, dplyr supplies five 'verbs' that cover most fundamental data  
| manipulation tasks: **select**(), **filter**(), **arrange**(), **mutate**(), and **summarize**().  

###Select
Select columns (in the order specified)  
- **select**(dataset, column, column, column, ...)
- **select**(dataset, startColumn : endColumn)
- **select**(dataset, -removeColumn)

###Filter
Select rows by conditional
- **filter**(dataset, cond 1, cond 2, ...)
- **filter**(dataset, cond1 | cond 2)

###Arrange
Sort rows ascending or descending or mix
- **arrange**(dataset, column, ...)
- **arrange**(dataset, desc(column), ...)

###Mutate
Create a new variable
- **mutate**(dataset, newVar = calculation)
- mutate(dataset, newVar = col1 / 20)

###Summarize

- **summarize**(dataset, varName = mean(col1))
- 

