improving deep neural networks

* split data into train, validation and test sets
* training a large enough network with regularization gets rid of bias variance tradeoff
* dropout regularization
  * ignore few nodes from each layer for a given example
  * no need to use dropout during prediction on test data
* other regularization techniques
  * data augmentation
  * early stopping
  * use L2 regualrization 
* vanishing and exploding gradients
  * may occur in very deep NN
  * depends on the values of weights
  * to fix initialize weights with variance as follows (n = no. neurons in previous layer)
    * W(layer) = random * sqrt(variance)
    * tanh => 1 / n OR  2 / (n + n_current_layer)
    * relu => 2 / n

* validate implementation of backpropagation using gradient checking
  * manual computation of partial derivative and compare with calculated partial derivatives
  * the difference need to be very little if implementation is correct
  * gradient chceking does not work with dropout

* improving speed of gradient descent
  * minibatch gradient descent
    * when training data is too large it takes to long to train
    * update parameters after processing few examples instead of complete training set
    * choosing minibatch size
      * = training size => batch gradient descent
      * = 1 => stochastic gradient descent
      * minibatch size should not be too large or too small
      * if small training set use batch gradient descent
      * 64 <= minibatch size <= 512
      * minibatch size should fit in memory

  * exponentially weighted averages
    * avg(t) = beta * avg(t - 1) + (1 - beta) * value(t)
  * bias correction in exponentially weighted averages
    * bias_corr_avg(t) = avg(t) / (1 - beta ^ t)

  * gradient descent with momentum
    * avoid oscillation and use large learning rate to improve speed of convergence
    * compute weighted average of weights, and biases
    * use weighted averages while updating weights
    * generally use beta = 0.9 for exponentially weighted averages and we may use bias correction as well

  * RMSProp
    * avoid oscillation and use large learning rate to improve speed of convergence
    * updates to weights are different as we did with momentum

  * adam optimization algorithm
    * puts momentum  and RMSProp together
    * use with minibatch gradient descent
    * bias correction is often used
    * weight update includes terms of momentum and RMSProp
    * RMSProp hyperparameter is generally 0.999
    * adaptive moment estimation

  * learning rate decay
    * reduce learning rate over time
    * multiple methods (formulas)
    * should be lower on priority list most times just use constant learning rate

* local optima / saddle points
  * in some directions we are in minima but in other directions we are at maxima
  * in high dimensional spaces unlikely to get stuck in local minima
  * plateus
    * derivatives on these points are very close to zero
    * take very long to reach minima
  * plateus make learning very slow
    

