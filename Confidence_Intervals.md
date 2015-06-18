
If an observed mean falls within the confidence interval then H(0) is not rejected

Confidence Intervals for sample size of 1 and 2:  
http://amstat.tandfonline.com/doi/abs/10.1198/000313001750358400  
Turns out it's: x±9.68|x|

### Confidence Levels
- For 95%, the quantile used is 0.975 (0.025 for ech tail, 5% on both)
- For 90%, the quantile used id 0.95 (0.05 for each tail, 10% on both)

## Confidence Interval For Equal Variances
```{R}
mean_a <- 6
std_a <- 2
n_a <- 100

mean_b <- 4
std_b <- 0.5
n_b <- 100


sp <- sqrt( ( ( (n_a-1) * std_a^2) + ( (n_b-1) * std_b^2) ) / (n_a + n_b - 2) )
(mean_a - mean_b) + c(-1,1) * qt(0.95, (n_a + n_b -2)) * sp * (1/n_a + 1/n_b) ^ 0.5
```

### Compute confidence internal
```{R}
mean_a <- 1100
std_a <- 30
n_a <- 9
percentile = 0.95

mean_a + c(-1, 1) * qt(0.95, (n_a - 1)) * std_a * (1 / n_a)^ 0.5
```
