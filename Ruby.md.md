# Table Of Contents

Github    https://github.com/peterpih/Miscellaneous/blob/master/GITHUB.md

Swirl     https://github.com/peterpih/Miscellaneous/blob/master/SWIRL.md

Data Analysis and Visualization     http://training.bioinformatics.ucdavis.edu/docs/2012/05/DAV/

### Bayes Theorem

- P(A | B) = P(A & B)/ P(B)  probability of A given B

- P(A & B) = P(A | B) * P(B)


- P(B | A)  = P(B & A)/P(A)
            = P(A|B) * P(B) / P(A)

                              P(A) = P(A | B) * P(B) + P(A | ~B) * P(~B)

- P(B | A) = P(A | B) * P(B) / ( P(A | B) * P(B) + P(A | ~B) * P(~B) )


Confidence Interval for Equal Variances
```{R}
mean_a <- -3
std_a <- 1.5
n_a <- 9

mean_b <- 1
std_b <- 1.8
n_b <- 9

sp <- sqrt( ( ( (n_a-1) * std_a^2) + ( (n_b-1) * std_b^2) ) / (n_a + n_b - 2) )
(mean_a - mean_b) + c(-1,1) * qt(0.95, (n_a + n_b -2)) * sp * (1/n_a + 1/n_b) ^ 0.5
```
