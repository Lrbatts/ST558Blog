ST558Blog4
================
Landon Batts
2023-07-20

## Blog 4: Machine Learning Recap

My favorite method of using machine learning to fit models to data
involved using the caret package. This is because it is so flexible and
can fit 238 different kinds of models within a single function. I
personally enjoyed doing linear models on to data to get a grasp of how
variables directly impact the size of another. I will now fit a linear
model on the built in iris data set to investigate how sepal
width/length as well as petal width and plant species impact petal width
by training the data set with 80% of the data and then fitting a linear
model.

``` r
library(caret)
```

    ## Loading required package: ggplot2

    ## Loading required package: lattice

``` r
set.seed(111)
trainIndex <- createDataPartition(iris$Sepal.Length, p = 0.8, list = FALSE)
irisTrain <- iris[trainIndex, ]
irisTest <- iris[-trainIndex, ]

fit <- train(Petal.Length ~ ., data = irisTrain,
method = "lm",
preProcess = c("center", "scale"),
trControl = trainControl(method = "cv", number = 10))
fit
```

    ## Linear Regression 
    ## 
    ## 121 samples
    ##   4 predictor
    ## 
    ## Pre-processing: centered (5), scaled (5) 
    ## Resampling: Cross-Validated (10 fold) 
    ## Summary of sample sizes: 107, 110, 109, 110, 108, 109, ... 
    ## Resampling results:
    ## 
    ##   RMSE       Rsquared   MAE      
    ##   0.2676821  0.9795305  0.2117127
    ## 
    ## Tuning parameter 'intercept' was held constant at a value of TRUE

``` r
#The very high R squared means this was a good model
```
