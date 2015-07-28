###Logistic Regression

fit <- glm(y~., data=dataset, family="binomial")

###Calculating Odds
Using shuttle data in MASS data set, use = noauto,auto; wind=headwind,tailwind
```{R}
library(MASS)
library(caret)

head(shuttle, 5)
```
```{R}
fit <- glm(use~wind, data=shuttle, family="binomial")
fit
```
Output:
```
Call:  glm(formula = use ~ wind, family = "binomial", data = shuttle)

Coefficients:
(Intercept)     windtail  
   -0.25131     -0.03181  

Degrees of Freedom: 255 Total (i.e. Null);  254 Residual
Null Deviance:	    350.4 
Residual Deviance: 350.3 	AIC: 354.3
```
Intercept is **use**, windtail (-0.2831) = -0.03181 + -0.25131  
  
Alternatively, regressing without intercept:
```{R}
fit <- glm(use~wind-1, data=shuttle, family="binomial")
fit
```
Call:  glm(formula = use ~ wind - 1, family = "binomial", data = shuttle)

Coefficients:
windhead  windtail  
 -0.2513   -0.2831  

Degrees of Freedom: 256 Total (i.e. Null);  254 Residual
Null Deviance:	    354.9 
Residual Deviance: 350.3 	AIC: 354.3
```
Odds ( = -0.2513 / -2831
