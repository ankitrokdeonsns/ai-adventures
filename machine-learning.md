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
  7. high bias
    * if training set is small then model can fit the training data well. however cross validation error is usually high
    * if training set is large then training and cross validation error will be high
  8. high variance
    * if training set is small then model can fit the training data well. however cross validation error is usually high
    * if training set is large then training error is very low but cross validation error is much higher
  9. fix high bias
    * add more features
    * add polynomial features
    * decrease regularization
  10. fix high variance
    * get more training data
    * try less features
    * increase regularization
  Q. how to determine if cross validation error is much higher than training error? how much difference is acceptable?


