
[Logistic Regression](*logistic-regression-section)
[Calculating Odds Section](*calculating-odds-section)
[Variance Inflation Factor](*variance-inflation-factor)

<div id='logistic-regression-section'>
###Logistic Regression

fit <- glm(y~., data=dataset, family="binomial")

<div id='calculating-odds-section'>
###Calculating Odds

Odds Ratio: https://en.wikipedia.org/wiki/Odds_ratio

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

<div id='variance-inflation-section'>
###Variance Inflation

As predictors are added to a multi-linear regression, if they are correlated the variance of the coefficients increases

<div id='variance-inflation-factor>
###Variance Inflation Factor (VIF)

The amount of variance due to including a regressor that is correlatied with another regressor
```{R}
fit <- lm(y~x,data)
VIF(fit)
```
