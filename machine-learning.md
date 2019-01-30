* feature scaling
  1. gradient descent converges slowly on large ranges
  2. it converges faster if all features are on similar scale
  3. two techniques: feature scaling and mean normalization
  3. feature scaling (value / max - min) brings feature range between -1 and 1
  4. mean normalization (value - mean / max - min) or (value - mean / stddev) makes the mean of new values to be 0

* finding good learning rate
  1. learning rate too small => show convergence
  2. learning rate too large => may not converge
  3. error must reduce after each iteration
  4. plot error against no. of iteration for a given learning rate

* logistic regression
  1. linear model for classification
  2. compress outcome of W * X into [0, 1]
  3. use sigmoid / logistic function for this
  4. cost function: -y * log(h(x)) - (1 - y) * log(1 - h(x)) where h(x) is the hypothesis W * X

* underfitting, overfitting and regularization
  1. underfitting (high bias): hypothesis poorly fits training data. training error is high
  2. underfitting due to less no. of features / hypothesis too simple
  3. overfitting (high variance): hypothesis fits training data too well. training error is very low. test error is high
  4. overfitting due to too many features / complex hypothesis
  5. solution to overfitting: reduce no. of features or use regularization
  6. regularization: penalize weights that are too high

* bias vs variance
  1. if model performs poorly we need to identify if it is due to underfitting (high bias) or overfitting (high variance)
  2. split the data into train (60%), validation (20%) and test (20%)
  3. underfitting: train error is high and validation error is high. also train error ~ validation error
  4. overfitting: train error is low and validation error much higher than train error
  5. use regularization with different values of lambda (regularization parameter) 
  6. select best model where cross validation error is low and also test error is also low
  7. if there is no regularization then the model overfits, if there is too much regularization model underfits
  8. in case of classification we can also compute misclassification error
  9. high bias (plot error against train size)
    * if training set is small then model can fit the training data well. however cross validation error is usually high
    * if training set is large then training and cross validation error will be high
  10. high variance (plot error against train size)
    * if training set is small then model can fit the training data well. however cross validation error is usually high
    * if training set is large then training error is very low but cross validation error is much higher
  11. fix high bias
    * add more features
    * add polynomial features
    * decrease regularization
  12. fix high variance
    * get more training data
    * try less features
    * increase regularization
  Q. how to determine if cross validation error is much higher than training error? how much difference is acceptable?

* work prioritization
  1. error analysis
    * implement a simple model quickly
    * plot learning curves (error against training set size) to identify if we are suffering from high bias / high variance
    * manually look in to data points where alorithm is making errors to develop better features
    * have a numerical measure to evaluate algorithm
  2. handling skewed classes
    * only classification accuracy is not the right metric
    * precision and recall
    * precision = true positives / predicted positives , predicted positives = true positives + false positives
    * recall = true positives / actual positives, actual positives = true positives + false negatives
    * precision and recall are defined for the rare class being 1 and non rare class being 0
    * high precision and high recall is the best model
    * predict true if only we are very confident: high precision and low recall
    * avoid false negatives: high recall less precision
    * comparing precision and recall values for multiple algorithms: f1-score if large precision and recall both large
  3. how much data to train?
    * as training set size increases performance of algorithm generally improves
    * use algorithm with many parameters: low bias, if we have large training data then it is unlikely to overfit
    * training error ~ test error => good algorithm, did not overfit

  
