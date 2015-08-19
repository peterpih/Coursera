###Tidyr
http://vita.had.co.nz/papers/tidy-data.pdf  

| Tidy data is formatted in a standard way that facilitates exploration and analysis and works seamlessly with other tidy  
| data tools. Specifically, tidy data satisfies three conditions:  
|   
| 1) Each variable forms a column  
| 2) Each observation forms a row   
| 3) Each type of observational unit forms a table  

**Messy Data**  
1: Column headers are values, not variable names  
2: Variables are stored in both rows and columns  
3: A single observational unit is stored in multiple tables  
4: Multiple types of observational units are stored in the same table  
5: Multiple variables are stored in one column  

###Gather  
Gather and Spread are compliments

**gather*(dataset, key, value, col1:coln)

###Spread

###Separate  

**separate**(dataset, key, newCol)

###Chaining
```
cran %>%
  select(ip_id, country, package, size) %>%
  mutate(size_mb = size / 2^20) %>%
  filter(size_mb <= 0.5) %>%
  # Your call to arrange() goes here
    arrange(desc(size_mb))
```
```
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


