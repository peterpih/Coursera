###Coursera Help: https://learner.coursera.help/hc/en-us/requests/new  

###R Studio Cheatsheets  
https://www.rstudio.com/resources/cheatsheets/  

Hans Rosling Ted Talk: http://www.ted.com/talks/hans_rosling_shows_the_best_stats_you_ve_ever_seen?language=en  


# Table Of Contents

**R for Beginners**  http://cran.r-project.org/doc/contrib/Paradis-rdebuts_en.pdf

**R in Econometrics** http://cran.r-project.org/doc/contrib/Farnsworth-EconometricsInR.pdf

###R Tutorials
**QuickR** http://www.statmethods.net/

###Course Utilities
**Github**    https://github.com/peterpih/Miscellaneous/blob/master/GITHUB.md

**Swirl**     https://github.com/peterpih/Miscellaneous/blob/master/SWIRL.md

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
