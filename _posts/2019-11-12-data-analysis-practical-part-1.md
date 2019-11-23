---
title: "Data Analysis' Practices - PART 1"
date: 2019-11-12
tags: [data analysis, R]
categories: [data analysis]
excerpt: "Here we show the tools we'll use and study our first R script"
author_profile: false
mathjax: "true"
---

In this Practical Studies we will use the Anaconda Navigator with a Jupyter Lab to *[compile](https://kb.iu.edu/d/agsz)* our R scripts.

*Instructions:*
1. Follow the link to *[download](https://www.anaconda.com/distribution/)* and to *[set up](https://docs.anaconda.com/anaconda/navigator/tutorials/r-lang/)* your Jupyter Lab to compile R after you've installed the Anaconda Navigator.
2. Remember to *[download](https://github.com/lucastvms/lucastvms.github.io/blob/master/assets/datasets/Developers.zip)* the datasets, unzip and configure its path on the code.
3. One of the libraries we'll be loading uses the system variable JAVA_HOME. Please install the correct version of Java JRE into your PC and set correctly its JAVA_HOME. Access this *[link](https://www.r-statistics.com/2012/08/how-to-load-the-rjava-package-after-the-error-java_home-cannot-be-determined-from-the-registry/)* to know more about the error for not having the variable correctly setted (this site also has a link to download manually the Java JRE) and this *[link](https://stackoverflow.com/questions/2619584/how-to-set-java-home-on-windows-7)* to know how to set the JAVA_HOME variable correctly.

Here's our R script for the Jupyter Lab: *[Effectiveness](https://github.com/lucastvms/lucastvms.github.io/blob/master/assets/r-scripts/Effectiveness.ipynb)*. Download it to accompany our studies.

Let's begin our studies about the code.

## Libraries

```r
### Load Library ###
library(RWeka)
library(e1071)
library(gmodels)
#library(C50)
library(caret)
library(irr)
library(randomForest)
```

### *[RWeka](https://cran.r-project.org/web/packages/RWeka/index.html)*:
##### An R interface to Weka. Weka is a collection of machine learning algorithms for data mining tasks written in Java, containing tools for data pre-processing, classification, regression, clustering, association rules, and visualization.

### *[E1071](https://cran.r-project.org/web/packages/e1071/index.html)*:
##### Functions for latent class analysis, short time Fourier transform, fuzzy clustering, support vector machines, shortest path computation, bagged clustering, naive Bayes classifier, ...

### *[GModels](https://cran.r-project.org/web/packages/gmodels/index.html)*:
##### Various R programming tools for model fitting.

### *[C50](https://cran.r-project.org/web/packages/C50/index.html)*:
##### A C5.0 decision trees and rulebased models for pattern recognition that extend the work of Quinlan (1993, ISBN:1-55860-238-0).

### *[Caret](https://cran.r-project.org/web/packages/caret/index.html)*:
##### Misc functions for training and plotting classification and regression models.

### *[IRR](https://cran.r-project.org/web/packages/irr/index.html)*:
##### Coefficients of Interrater Reliability and Agreement for quantitative, ordinal and nominal data: ICC, Finn-Coefficient, Robinson's A, Kendall's W, Cohen's Kappa, ...

### *[randomForest](https://cran.r-project.org/web/packages/randomForest/index.html)*:
##### Classification and regression based on a forest of trees using random inputs, based on Breiman (2001) <[doi:10.1023A:1010933404324](https://link.springer.com/article/10.1023%2FA%3A1010933404324)>.

## Functions

##### Our Functions are based in the theory of the *[Confusion Matrix](https://www.geeksforgeeks.org/confusion-matrix-machine-learning/)*:

![alt]({{ site.url }}{{ site.baseurl }}/assets/images/data-analysis/confusion-matrix.png)
*Source: [GeeksforGeeks](https://www.geeksforgeeks.org/confusion-matrix-machine-learning/)*

Where,
* Class 1 : Positive
* Class 2 : Negative

##### Definition of the Terms:
* Positive (P) : Observation is positive (for example: is an apple).
* Negative (N) : Observation is not positive (for example: is not an apple).
* True Positive (TP) : Observation is positive, and is predicted to be positive.
* False Negative (FN) : Observation is positive, but is predicted negative.
* True Negative (TN) : Observation is negative, and is predicted to be negative.
* False Positive (FP) : Observation is negative, but is predicted positive.

A confusion matrix is a summary of prediction results on a classification problem.

The number of correct and incorrect predictions are summarized with count values and broken down by each class. This is the key to the confusion matrix.

The confusion matrix shows the ways in which your classification model is confused when it makes predictions.

It gives us insight not only into the errors being made by a classifier but more importantly the types of errors that are being made.

##### Let's continue to study our code:

### *[Precision](https://www.rdocumentation.org/packages/MLmetrics/versions/1.1.1/topics/Precision)*:
```r
# Precision
precision <- function(tp, fp){

  precision <- tp/(tp+fp)

  return(precision)
}
```

##### The precision can answer the following question: What proportion of positive identifications was actually correct?.

### *[Recall](https://www.rdocumentation.org/packages/caret/versions/6.0-84/topics/recall)*:
```r
# Recall
recall <- function(tp, fn){

  recall <- tp/(tp+fn)

  return(recall)
}
```

##### The recall can answer the following question: What proportion of actual positives was identified correctly?.

### *[F - Measure](https://www.rdocumentation.org/packages/PerfMeas/versions/1.2.1/topics/F.measures)*:
```r
# F-measure
f_measure <- function(tp, fp, fn){

  f_measure <- (2*precision(tp,fp)*recall(tp,fn))/(recall(tp,fn) + precision(tp, fp))

  return(f_measure)
}
```

##### F-Measure is a measure of a test’s accuracy.


### *[Measures](https://www.rdocumentation.org/packages/Momocs/versions/1.2.9/topics/measure)*:
```r
measures <- function(test, pred){

  true_positive <- 0
  true_negative <- 0
  false_positive <- 0
  false_negative <- 0

  for(i in 1:length(pred)){
    if(test[i] == TRUE && pred[i] == TRUE){
      true_positive <- true_positive + 1
    }else if(test[i] == FALSE && pred[i] == FALSE){
      true_negative <- true_negative + 1
    }else if(test[i] == FALSE && pred[i] == TRUE){
      false_negative <- false_negative + 1
    }else if(test[i] == TRUE && pred[i] == FALSE){
      false_positive <- false_positive + 1
    }
  }

  measures <- c(precision(true_positive,false_positive),
                recall(true_positive,false_negative),
                f_measure(true_positive,false_positive,false_negative))

  return(measures)
}
```

##### Then, in information retrieval, the positive predictive value is called precision, and sensitivity is called recall. The F-score can be used as a single measure of performance of the test for the positive class. The F-score is the harmonic mean of precision and recall.

### Techniques

##### *Example:*
```r
executeJ48 <- function(dataset, folds){
  results <- lapply(folds, function(x) {
    train <- dataset[-x, ]
    test <- dataset[x, ]
    model <- J48(train$Smell~ ., data = train)
    pred <- predict(model, test)

    results <- measures(test$Smell, pred)

    return(results)
  })

}
```
##### Notice the attribution to *model*

##### In this section we run a lot of models to evaluate data using functions of our different libraries. Notice that each of them representes a different techinque (model).

### DCL Analysis
DCL stands for Detection, Classification and Localization

```r
### DCL Analysis ###

techniques <- c("J48", "NaiveBayes", "SVM", "oneR", "JRip", "RandomForest", "SMO")

smells <- c("FE", "DCL", "GC", "II","LM", "MC", "MM", "PO","RB","SG")

# SS
#developers <- c(2, 7, 25, 28, 31, 32, 69, 86, 92, 96, 106, 107)


developers <- data.frame(c(1, 5, 6, 9, 55, 58, 60, 84, 97, 99, 101, 103),
                         c(2, 17, 18, 19, 21, 22, 27, 30, 77, 86, 93, 104),
                         c(1, 9, 13, 15, 16, 61, 62, 66, 84, 94, 102, 103),
                         c(2, 7, 21, 22, 24, 25, 28, 86, 104, 110, 111, 124),
                         c(41, 42, 43, 45, 46, 47, 49, 51, 64, 74, 81, 95),
                         c(5, 6, 10, 52, 53, 55, 58, 60, 91, 97, 99, 101),
                         c(8, 11, 39, 40, 41, 42, 43, 45, 46, 47, 74, 81),
                         c(46, 47, 49, 51, 52, 53, 64, 74, 91, 95, 105, 109),
                         c(13, 15, 16, 17, 18, 19, 30, 61, 94, 102, 111, 112),
                         c(5, 49, 51, 52, 53, 55, 56, 64, 91, 95, 99, 105))

colnames(developers) <- smells

list_of_results <- list()

for(j in 1:10){

  print(colnames(developers)[j])

  path <- paste("C:/Users/Lucas/Documents/GitHub/lucastvms.github.io/assets/datasets/Developers/",colnames(developers)[j],"/",colnames(developers)[j]," - ",sep="")

  results <- data.frame(0,0,0, 0, 0,0,0)


  for(q in 1:12){

    dev_path <- paste(path,developers[q,j],".csv",sep="")
    dataset <- read.csv(dev_path, stringsAsFactors = FALSE)

    dataset$Smell <- factor(dataset$Smell)

    set.seed(3)
    folds <- createFolds(dataset$Smell, k =5)

    resultsJ48 <- executeJ48(dataset, folds)
    partial_results <- rowMeans(as.data.frame(resultsJ48), na.rm = TRUE)

    resultsNaiveBayes <- executeNaiveBayes(dataset, folds)
    partial_results <- rbind(partial_results, rowMeans(as.data.frame(resultsNaiveBayes), na.rm = TRUE) )

    resultsSVM <- executeSVM(dataset, folds)
    partial_results <- rbind(partial_results, rowMeans(as.data.frame(resultsSVM), na.rm = TRUE))

    resultsOneR <- executeOneR(dataset, folds)
    partial_results <- rbind(partial_results, rowMeans(as.data.frame(resultsOneR), na.rm = TRUE))

    resultsJRip <- executeJRip(dataset, folds)
    partial_results <- rbind(partial_results, rowMeans(as.data.frame(resultsJRip), na.rm = TRUE))

    resultsRandomForest <- executeRandomForest(dataset, folds)
    partial_results <- rbind(partial_results, rowMeans(as.data.frame(resultsRandomForest), na.rm = TRUE))

    resultsSMO <- executeSMO(dataset, folds)
    partial_results <- rbind(partial_results, rowMeans(as.data.frame(resultsSMO), na.rm = TRUE))

    rownames(partial_results) <- c("J48", "NaiveBayes", "SVM", "oneR", "JRip", "RandomForest","SMO")
    colnames(partial_results) <- c("Precision", "Recall", "F-measure")

    print(paste("Developer",developers[ q, j]))

    print(partial_results)

    results <- rbind(results, partial_results[,3])
  }

  results <- results[-1,]
  rownames(results) <- developers[ ,j]
  colnames(results) <- techniques
  results[,] <- lapply(results,function(x){ x[is.nan(x)]<-0;return(x)})

  list_of_results[[j]] <- results

}

print(list_of_results)

for(smell in 1:10){
  print(smells[smell])

  print(list_of_results[[smell]])
}


results_mean <-     matrix(c(mean(list_of_results[[1]]$J48),
                             mean(list_of_results[[1]]$NaiveBayes),
                             mean(list_of_results[[1]]$SVM),
                             mean(list_of_results[[1]]$oneR),
                             mean(list_of_results[[1]]$JRip),
                             mean(list_of_results[[1]]$RandomForest),
                             mean(list_of_results[[1]]$SMO)),
                           nrow = 1,
                           ncol = 7)

for(smell in 2:10){
  results_mean <- rbind(results_mean, c(mean(list_of_results[[smell]]$J48),
                                        mean(list_of_results[[smell]]$NaiveBayes),
                                        mean(list_of_results[[smell]]$SVM),
                                        mean(list_of_results[[smell]]$oneR),
                                        mean(list_of_results[[smell]]$JRip),
                                        mean(list_of_results[[smell]]$RandomForest),
                                        mean(list_of_results[[smell]]$SMO)))
}

results_mean


colnames(results_mean) <- techniques
rownames(results_mean) <- colnames(developers)
results_mean <- t(results_mean)
results_mean

barplot(results_mean,
        main="Code Smells x Effectiveness",
        ylab="Effectiveness",
        xlab="Techniques",
        col=c("red", "yellow", "green", "violet", "orange", "blue", "pink"),
        ylim = c(0, 1),
        #legend = rownames(results_mean),
        beside=TRUE)

```

##### This section represents the results of our models doing a DCL Analysis. Here we basically do the analysis using the data gathered from our models. You can change the code in this section depending on your objective. If you have any questions about R, please take some time to experience the [R Documentation](https://www.rdocumentation.org/).
