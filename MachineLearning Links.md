https://www.youtube.com/watch?v=TK4qLwTye_s  

http://neuralnetworksanddeeplearning.com/chap1.html  

Ebook:  
http://www.iro.umontreal.ca/~bengioy/dlbook/  


Standford Machine Learning Videos:  
cs229.stanford.edu  
20 lectures: https://www.youtube.com/watch?v=UzxYlbK2c7E&list=PLA89DCFA6ADACE599  

#Video Links:
###Machine Learning: The Basics, with Ron Bekkerman
https://www.youtube.com/watch?v=wjTJVhmu1JM  

Three major subgroup of Machine Learning:
1. Classification - which data are in defined groups, know classification beforehand  
2. Clustering - which data points sits next to each other  
3. Regression - kind of like a ranking system  

Classification and Clustering look similar, but technology is very different
Clustering and Regression look different, but tecnhology is very similar  

Machine Learning is not an exact science, but is that bad?  

For **classification** major problem is getting the labelled data (classified) for training

**Implicit feedback** track click-through  
Data skewness when **explcit feedback** (yes or no) is given  

**K-nearest neighbor** new label based on what neighbor labels are  
Main weakness is all the data still needs to be compared  

**Support Vector Machine** 
**Maximum margin classifier** - maximize distance from each group  
The data points which touch the the MMC boundary are the support vectors  
SVM are very good at binary problems, what happens when there are 3 groups?  

High dimensional rpoblems are non-intuitive, can not be visualized in one's head
In high dimernsion, classes are linearly separated, can find a hyperplane to separate  
Use SVM when there is not too much training data, taining an SVMis very heavy  
SVMs are good if there is geometry in your task, machine vision  
Use SVM when high precision is crticial
The parameters will need to be tuned

**Decision Trees**  
Determining threshold for branching is were the voodoo is  

If you can find the **right features**, the learning technique doesn't need to be sophisticated  

**Boosted Decision Trees**  
Build a decsion forest iteratively, choose new trees for cases not yet covered by the forest  
This is a very powerful technique  
Use **boosted decision trees** in high dimensional data (lots of features) (text classification)  
Not good if data is highly skewed  

**Logistic Regression**  
Called "regression" because the technique is similar to regression, but used differently  
Use when the model has a probabilistic setup
Use whent he number of features is pretty small, will tell you which features are important  
Has good explainability, training is fast, but not very precise  

###Clustering  
Builds "coherent" groups of data  
Look at representative data point in each cluster  
Setup **centroids** (seed center of clusters  
Clustering is inherently inaccurate  

LinkedIn case study:  
Use most common phreases rather than job titles to cluster on  

###Scaling Up Machine Learning, with Ron Bekkerman
https://www.youtube.com/watch?v=pyac2Xm38qQ  


###Introduction to Data Analysis using Machine Learning:  
https://www.youtube.com/watch?v=U4IYsLgNgoY  


