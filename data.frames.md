
This example is from: http://stackoverflow.com/questions/1299871/how-to-join-merge-data-frames-inner-outer-left-right

It shows different ways to merge different dataframes

- Inner join - merge(df1, df2, by = "CustomerId"")
- Outer join - merge(x = df1, y = df2, by = "CustomerId", all = TRUE)
- Left outer - merge(x = df1, y = df2, by = "CustomerId", all.x = TRUE)
- Right outer - merge(x = df1, y = df2, by = "CustomerId", all.y = TRUE)
- Cross join - merge(x = df1, y = df2, by = NULL)

Here is the sample data:


```r
df1 = data.frame(CustomerId = c(1:6), Product = c(rep("Toaster", 3), rep("Radio", 3)))
df2 = data.frame(CustomerId = c(2, 4, 6), State = c(rep("Alabama", 2), rep("Ohio", 1)))
```


```r
df1
```

```
##   CustomerId Product
## 1          1 Toaster
## 2          2 Toaster
## 3          3 Toaster
## 4          4   Radio
## 5          5   Radio
## 6          6   Radio
```

```r
df2
```

```
##   CustomerId   State
## 1          2 Alabama
## 2          4 Alabama
## 3          6    Ohio
```

### Inner join - intersection of both data frames


```r
merge(df1, df2, by = "CustomerId")
```

```
##   CustomerId Product   State
## 1          2 Toaster Alabama
## 2          4   Radio Alabama
## 3          6   Radio    Ohio
```

### Outer join - everything together


```r
merge(x = df1, y = df2, by = "CustomerId", all = TRUE)
```

```
##   CustomerId Product   State
## 1          1 Toaster    <NA>
## 2          2 Toaster Alabama
## 3          3 Toaster    <NA>
## 4          4   Radio Alabama
## 5          5   Radio    <NA>
## 6          6   Radio    Ohio
```

### Left outer - only members on the left hand side (x)

```r
merge(x = df1, y = df2, by = "CustomerId", all.x = TRUE)
```

```
##   CustomerId Product   State
## 1          1 Toaster    <NA>
## 2          2 Toaster Alabama
## 3          3 Toaster    <NA>
## 4          4   Radio Alabama
## 5          5   Radio    <NA>
## 6          6   Radio    Ohio
```

### Right outer - only members on the right hand side (y)

```r
merge(x = df1, y = df2, by = "CustomerId", all.y = TRUE)
```

```
##   CustomerId Product   State
## 1          2 Toaster Alabama
## 2          4   Radio Alabama
## 3          6   Radio    Ohio
```
### Cross join - all permutations

```r
merge(x = df1, y = df2, by = NULL)
```

```
##    CustomerId.x Product CustomerId.y   State
## 1             1 Toaster            2 Alabama
## 2             2 Toaster            2 Alabama
## 3             3 Toaster            2 Alabama
## 4             4   Radio            2 Alabama
## 5             5   Radio            2 Alabama
## 6             6   Radio            2 Alabama
## 7             1 Toaster            4 Alabama
## 8             2 Toaster            4 Alabama
## 9             3 Toaster            4 Alabama
## 10            4   Radio            4 Alabama
## 11            5   Radio            4 Alabama
## 12            6   Radio            4 Alabama
## 13            1 Toaster            6    Ohio
## 14            2 Toaster            6    Ohio
## 15            3 Toaster            6    Ohio
## 16            4   Radio            6    Ohio
## 17            5   Radio            6    Ohio
## 18            6   Radio            6    Ohio
```



