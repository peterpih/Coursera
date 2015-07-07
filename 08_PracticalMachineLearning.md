#Caret Package  
http://caret.r-forge.r-project.org/

**Caret tutorials:**  
http://www.edii.uclm.es/~useR-2013/Tutorials/kuhn/user_caret_2up.pdf  
http://cran.r-project.org/web/packages/caret/vignettes/caret.pdf  

**A paper introducing the caret package**  
http://www.jstatsoft.org/v28/i05/paper  

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
folds <- createTimeSlices(y=tme,initialWindow=20,
                          horizon=10)
names(folds)
```

