```
mod1<-train(y~.,data=x,method='whatever',model=FALSE) 
```

***Attribution: Patricia Ellen Tressel CTA (pml-031)***  
The "model" parameter appears to be for glm rather than rf, which is what Jason is using -- it doesn't control what caret is doing. 

There are three trainControl parameters that can be set to tell caret not to save extra information.  The only "downside" is that if you want to get the accuracy *on the training set*, e.g. if you want to check for overfitting, then you'll need to supply the training set in predict as newdata.  Not exactly a problem.  Here are the parameters -- include these along with whatever other trainControl parameters you have:

returnData=FALSE, returnResamp="none", savePredictions=FALSE

randomForest does not appear to hold onto unneeded information.  However, you may be able to reduce ntree or mtry and still have good performance.  Can also adjust other settings like nodesize and maxnodes.  You can have caret's train search for good settings -- see tuneGrid and tuneLength.  If you have to restrict the size of the model, you can specify the range of values to try for (e.g.) ntree in tuneGrid.

***Attribution: Ray Jones CTA (pml-032)***  
A couple of points:

(1) Typically you'd train against the majority of the data (70-80%) and test against the rest (20-30%).

(2) trainControl is how you control the model tuning / cross-validation in caret - this is very important - my guess is that with your model, if you are using the default settings, you are spending the majority of execution time and memory in the cross-validation. When I did this exercise I found I could cut this down dramatically and not harm the accuracy of my prediction (I mean taking the execution time from > 3 hours to around 20 mins). I did this using trainControl.

Useful stackoverflow link:  
http://stackoverflow.com/questions/6543999/why-is-caret-train-taking-up-so-much-memory  

***Attribution: Patricia Ellen Tessel CTA pml-031***  
If you're calling randomForest directly, you can use the ntree parameter.  Or, you can pass the ntree parameter to randomForest in the train call.  In the ?train help info, you'll see ... in the call -- the parameters that train doesn't recognize, it just passes through to randomForest.  So look at ?randomForest to see its options.  If you're using train, you may also want to control what values it tried for tuning the parameters -- see tuneGrid and tuneLength.

Now, what value you should set ntree to is a whole 'nother thing.  As they say in the help info, don't set it too low.  You can try out different values, to see how low you can set it, and still get good enough performance.  ntree will very directly affect the size of the model object, if that is a concern.

