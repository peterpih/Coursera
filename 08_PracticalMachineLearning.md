#Caret Package  

###Table of Contents
1. [Useful Links](#useful-links)
1. [Caret Functionality](#caret-functionality)
2. [Data Splitting](#data-splitting)
  + [K-Fold Splitting](#k-fold-splitting)
  + [Resampling](#resampling)
  + [Time Slicing](#time-slicing)
3. [Plotting](#plotting)
4. [Tables](#tables)
5. [Preprocessing](#preprocessing)
6. [Principle Component Analysis](*principle-component-analysis)

###Useful Links
http://caret.r-forge.r-project.org/

**Caret tutorials:**  
http://www.edii.uclm.es/~useR-2013/Tutorials/kuhn/user_caret_2up.pdf  
http://cran.r-project.org/web/packages/caret/vignettes/caret.pdf  

**A paper introducing the caret package**  
http://www.jstatsoft.org/v28/i05/paper  

**Plotting**  
ggplot2 tutorial: http://rstudio-pubs-static.s3.amazonaws.com/2176_75884214fc524dc0bc2a140573da38bb.html  
caret visualization: http://caret.r-forge.r-project.org/visualizations.html  

[[Top]](#caret-package)  

###CARET FUNCTIONALITY
- Some preprocessing (cleaning)
  + preProcess
- Data splitting
  + createDataPartition
  + createResample
  + createTimeSlices
- Training/testing functions
  + train
  + predict
- Model comparison
  + confusionMatrix

###SPAM Data Set
These examples use the SPAM data set
```{R}
library(caret); library(kernlab); data(spam)
```

###DATA SPLITTING
```{R}
library(caret); library(kernlab); data(spam)
inTrain <- createDataPartition(y=spam$type, p=0.75, list=FALSE)
training <- spam[inTrain,]
testing <- spam[-inTrain,]
dim(training)
```
<div id='k-fold-splitting'/>
**K-Fold Splitting** return train data (returnTrain=TRUE)
```{R}
set.seed(32323)
folds <- createFolds(y=spam$type, k=10, list=TRUE, returnTrain=TRUE)
sapply(folds,length)
```

Return test data by setting **returnTrain=FALSE**

```{R}
set.seed(32323)
folds <- createFolds(y=spam$type, k=10, list=TRUE, returnTrain=FALSE)
sapply(folds,length)
```
<div id='resampling'/>
**Resampling**
```{R}
set.seed(32323)
folds <- createResample(y=spam$type, times=10, list=TRUE)
sapply(folds,length)
```
<div id='time-slicing'/>
**Time Slicing**
```{R}
set.seed(32323)
tme <- 1:1000
folds <- createTimeSlices(y=tme, initialWindow=20, horizon=10)
names(folds)
```

[[Top]](#caret-package)  

###PLOTTING
```{R}
install.packages("ISLR")
install.packages("caret")
library(ISLR); library(ggplot2); library(caret);
data(Wage)
summary(Wage)
```
**Setup Data**
```{R}
inTrain <- createDataPartition(y=Wage$wage, p=0.7, list=FALSE)
training <- Wage[inTrain,]
testing <- Wage[-inTrain,]
dim(training); dim(testing)
```
**Feature Plot (caret)**
```{R}
featurePlot(x=training[,c("age",  "education", "jobclass")], y = training$wage, plot="pairs")
```
**qplot (ggplot2)**
```{R}
qplot(age,wage,data=training)
```
**qplot with colour**
```{R}
qplot(age,wage,colour=jobclass,data=training)
```
**qplot add regression smoothers**
```{R}
qq <- qplot(age,wage,colour=education,data=training)
qq +  geom_smooth(method='lm',formula=y~x)
```
**Density Graph**
```{R}
qplot(wage,colour=education,data=training,geom="density")
```

###cut2 - MAKING FACTORS
```{R}
install.packages("Hmsic")
library(Hmisc)
cutWage <- cut2(training$wage,g=3)
table(cutWage)
```
**Box plot**
```{R}
p1 <- qplot(cutWage,age, data=training, fill=cutWage, geom=c("boxplot"))
p1
```
**Box plot with points (jitter)**
```{R}
p2 <- qplot(cutWage,age, data=training, fill=cutWage, geom=c("boxplot","jitter"))
# grid.arrange(p1,p2,ncol=2)
```

###TABLES
```{R}
t1 <- table(cutWage,training$jobclass)
t1
```

**Notes and further reading**
- Make your plots only in the **training set  **
  + **Don't use the test set for exploration!**  
- Things you should be looking for  
  + Imbalance in outcomes/predictors
  + Outliers
  + Groups of points not explained by a predictor
  + Skewed variables

ggplot2 tutorial: http://rstudio-pubs-static.s3.amazonaws.com/2176_75884214fc524dc0bc2a140573da38bb.html  
caret visualization: http://caret.r-forge.r-project.org/visualizations.html  

[[Top]](#caret-package)  

###PREPROCESSING
Graph distribution of SPAM data set  
Capital rng length, high skewed distribution
```{R}
install.packages("kernlab")
library(caret); library(kernlab); data(spam)
inTrain <- createDataPartition(y=spam$type, p=0.75, list=FALSE)
training <- spam[inTrain,]
testing <- spam[-inTrain,]
hist(training$capitalAve,main="",xlab="ave. capital run length")
```
```{R}
mean(training$capitalAve)
sd(training$capitalAve)
```
**Standardizing training set**
Subtract mean and divide by standard deviation
```{R}
trainCapAve <- training$capitalAve
trainCapAveS <- (trainCapAve  - mean(trainCapAve))/sd(trainCapAve) 
mean(trainCapAveS)
sd(trainCapAveS)
```
**Standardizing training set - preProcess function**
Use all of the training set data except for data point 58  
"center","scale" for normalizing
```{R}
preObj <- preProcess(training[,-58],method=c("center","scale"))
trainCapAveS <- predict(preObj,training[,-58])$capitalAve
mean(trainCapAveS)
sd(trainCapAveS)
```
**Standardizing - test set**
need to use the **mean(trainCapAve)** and **sd(trainCapAve)** from the training set
```{R}
testCapAve <- testing$capitalAve
testCapAveS <- (testCapAve  - mean(trainCapAve))/sd(trainCapAve) 
mean(testCapAveS)
sd(testCapAveS)
```
**Standardizing test set - preProcess function**
Use preObj from preProcess of training set to standardize test set  
Mean and std will be different  than "usual way" die to different meadn and std
```{R}
testCapAveS <- predict(preObj,testing[,-58])$capitalAve
mean(testCapAveS)
sd(testCapAveS)
```

**Standardizing - preProcess argument**
```{R}
install.packages("e1071")
set.seed(32343)
modelFit <- train(type ~., data=training, preProcess=c("center","scale"),method="glm")
modelFit
```

**Standardizing - Box-Cox transforms**
Box-Cox tranform takes continuous data and makes looks like normal data
Esitmates parameters usnig Maximum Likelihood
Good for highly skewed variables
```{R}
preObj <- preProcess(training[,-58],method=c("BoxCox"))
trainCapAveS <- predict(preObj,training[,-58])$capitalAve
par(mfrow=c(1,2)); hist(trainCapAveS); qqnorm(trainCapAveS)
```

**Standardizing - Imputing data**
K-Nearest Neighbor Imputation
```{R}
install.packages("RANN")
set.seed(13343)

# Make some values NA
training$capAve <- training$capitalAve
selectNA <- rbinom(dim(training)[1],size=1,prob=0.05)==1
training$capAve[selectNA] <- NA

# Impute and standardize
preObj <- preProcess(training[,-58],method="knnImpute")
capAve <- predict(preObj,training[,-58])$capAve

# Standardize true values
capAveTruth <- training$capitalAve
capAveTruth <- (capAveTruth-mean(capAveTruth))/sd(capAveTruth)
```
Check the imputation
```{R}
quantile(capAve - capAveTruth)              # entire population
quantile((capAve - capAveTruth)[selectNA])  # the replaced NAs
quantile((capAve - capAveTruth)[!selectNA]) # the non NAs
```
###Notes and further reading
- Training and test must be processed in the same way
  + only use any transformations on 
- Test transformations will likely be imperfect
  + Since transformations are based on the training data set
  + Especially if the test/training sets collected at different times
- Careful when transforming factor variables!
  + These are based on continuous variables

**preprocessing with caret:** http://caret.r-forge.r-project.org/preprocess.html  

[[Top]](#caret-package)  

###PRINCIPLE COMPUNENT ANALYSIS
Using SPAM dataset  

**Correlated predictors**
```{R}
library(caret); library(kernlab); data(spam)
inTrain <- createDataPartition(y=spam$type, p=0.75, list=FALSE)
training <- spam[inTrain,]      # get training subset
testing <- spam[-inTrain,]      # get training subset

M <- abs(cor(training[,-58]))   # correlation of all variables except for 58 (solution column)
diag(M) <- 0                    # remove correlation with itself
which(M > 0.8,arr.ind=T)        # which have high correlation
```
which columns are they?
```{R}
names(spam)[c(34,32)]
```
plot against each other to see correlation
```{R}
plot(spam[,34],spam[,32])
```
**Basic PCA idea**
- We might not need every predictor, maybe combine some variables
- A weighted combination of predictors might be better
- We should pick this combination to capture the "most information" possible
- Benefits
  + Reduced number of predictors
  + Reduced noise (due to averaging)

**We could rotate the plot**
We can tranform the X and Y variables, when plotted will show most of variability happens in the X axis
```{R}
X <- 0.71*training$num415 + 0.71*training$num857
Y <- 0.71*training$num415 - 0.71*training$num857
plot(X,Y)
```
Most if the values along the X axis, and clusterd around Y=0  
So the sum is more useful  

**Related problems**
You have multivariate variables X1,…,Xn so X1=(X11,…,X1m)  
Find a new set of multivariate variables that are uncorrelated and explain as much variance as possible.  
If you put all the variables together in one matrix, find the best matrix created with fewer variables (**lower rank**) that explains the original data.  
The first goal is statistical and the second goal is data compression.  


**Related solutions - PCA/SVD**
SVD (Singular Value Decomposition)  

If X is a matrix with each variable in a column and each observation in a row then the SVD is a "matrix decomposition"  
```
X = U D V^T  
```
where the columns of U are orthogonal (left singular vectors), the columns of V are orthogonal (right singluar vectors) and D is a diagonal matrix (singular values).  V explains most of the variance 

PCA

The principal components are equal to the right singular values if you first scale (subtract the mean, divide by the standard deviation) the variables.

**Principal components in R - prcomp**
```{R}
smallSpam <- spam[,c(34,32)]
prComp <- prcomp(smallSpam)
plot(prComp$x[,1],prComp$x[,2])
```
```{R}
prComp$rotation
```
