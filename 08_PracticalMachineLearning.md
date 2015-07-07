#Caret Package  
http://caret.r-forge.r-project.org/

**Caret tutorials:**  
http://www.edii.uclm.es/~useR-2013/Tutorials/kuhn/user_caret_2up.pdf  
http://cran.r-project.org/web/packages/caret/vignettes/caret.pdf  

**A paper introducing the caret package**  
http://www.jstatsoft.org/v28/i05/paper  

**Plotting**  
ggplot2 tutorial: http://rstudio-pubs-static.s3.amazonaws.com/2176_75884214fc524dc0bc2a140573da38bb.html  
caret visualization: http://caret.r-forge.r-project.org/visualizations.html  

###Caret functionality
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

**Resampling**
```{R}
set.seed(32323)
folds <- createResample(y=spam$type, times=10, list=TRUE)
sapply(folds,length)
```

**Time Slices**
```{R}
set.seed(32323)
tme <- 1:1000
folds <- createTimeSlices(y=tme, initialWindow=20, horizon=10)
names(folds)
```

###PLotting
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
**Feature Plot (craret)**
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

###cut2 - Making Factors
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

###Tables
```{R}
t1 <- table(cutWage,training$jobclass)
t1
```

###Notes and further reading
- Make your plots only in the **training set  **
  + **Don't use the test set for exploration!**  
- Things you should be looking for  
  + Imbalance in outcomes/predictors
  + Outliers
  + Groups of points not explained by a predictor
  + Skewed variables

ggplot2 tutorial: http://rstudio-pubs-static.s3.amazonaws.com/2176_75884214fc524dc0bc2a140573da38bb.html  
caret visualization: http://caret.r-forge.r-project.org/visualizations.html  
