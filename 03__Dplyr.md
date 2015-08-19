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
Create a new variable by row
- **mutate**(dataset, newVar = calculation)
- mutate(dataset, newVar = col1 / 20)

###Summarize
- **summarize**(dataset, varName = mean(col1))

**group_by**(dataset, column)

```
pack_sum <- summarize(by_package,
                      count = n(),
                      unique = n_distinct(ip_id),
                      countries = n_distinct(country),
                      avg_bytes = mean(size))
```
| The 'count' column, created with n(), contains the total number of rows (i.e. downloads) for each package. The 'unique'  
| column, created with n_distinct(ip_id), gives the total number of unique downloads for each package, as measured by the  
| number of distinct ip_id's. The 'countries' column, created with n_distinct(country), provides the number of countries in  
| which each package was downloaded. And finally, the 'avg_bytes' column, created with mean(size), contains the mean  
| download size (in bytes) for each package.  

###Piping
```{R}
by_package <- group_by(cran, package)
pack_sum <- summarize(by_package,
                      count = n(),
                      unique = n_distinct(ip_id),
                      countries = n_distinct(country),
                      avg_bytes = mean(size))

# Here's the new bit, but using the same approach we've
# been using this whole time.

top_countries <- filter(pack_sum, countries > 60)
result1 <- arrange(top_countries, desc(countries), avg_bytes)
```

```{R}
result2 <-
  arrange(
    filter(
      summarize(
        group_by(cran,
                 package
        ),
        count = n(),
        unique = n_distinct(ip_id),
        countries = n_distinct(country),
        avg_bytes = mean(size)
      ),
      countries > 60
    ),
    desc(countries),
    avg_bytes
  )

print(result2)
```

***Using chaining***
```{R}
result3 <-
  cran %>%
  group_by(package) %>%
  summarize(count = n(),
            unique = n_distinct(ip_id),
            countries = n_distinct(country),
            avg_bytes = mean(size)
  ) %>%
  filter(countries > 60) %>%
  arrange(desc(countries), avg_bytes)

# Print result to console
print(result3)
```
```
# We want the values in the class columns to be
# 1, 2, ..., 5 and not class1, class2, ..., class5.
#
# Use the mutate() function from dplyr along with
# extract_numeric(). Hint: You can "overwrite" a column
# with mutate() by assigning a new value to the existing
# column instead of creating a new column.
#
# Check out ?mutate and/or ?extract_numeric if you need
# a refresher.
#
students3 %>%
  gather(class, grade, class1:class5, na.rm = TRUE) %>%
  spread(test, grade) %>%
  ### Call to mutate() goes here %>%
  mutate(class=extract_numeric(class)) %>%
  print
```
```
# Accomplish the following three goals:
#
# 1. select() all columns that do NOT contain the word "total",
# since if we have the male and female data, we can always
# recreate the total count in a separate column, if we want it.
# Hint: Use the contains() function, which you'll
# find detailed in 'Special functions' section of ?select.
#
# 2. gather() all columns EXCEPT score_range, using
# key = part_sex and value = count.
#
# 3. separate() part_sex into two separate variables (columns),
# called "part" and "sex", respectively. You may need to check
# the 'Examples' section of ?separate to remember how the 'into'
# argument should be phrased.
#
sat %>%
  select(-contains("total")) %>%
  gather(part_sex, count, -score_range) %>%
  ### <Your call to separate()> %>%
    separate(part_sex, c("part", "sex") ) %>%
  print
```
