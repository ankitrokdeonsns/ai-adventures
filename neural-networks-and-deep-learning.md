* for sigmoid function for large inputs gradient vanishes, relu does not have this issue hence gradient descent works much better with relu
* activation functions
  * sigmoid
    * choose if output is a binary classification problem / output should lie between 0 and 1
  * tanh (brings the mean of activation to 0) => better than sigmoid almost always
    * if input to tanh is very large or very small gradient changes very slowly
    * always better than sigmoid
  * relu
    * choose almost always
    * gradient is 0 if input is negative (works fine in practice)
  * leaky relu
  
* why need a non linear activation function ?
  * if we dont use a activation function the output is just a linear function of input irrespective of number of hidden layers
  
* initialize weights of neural network randomly
  * why not initialize with zeros?
    * all hidden units compute the same function
    * we need different hidden units to compute different functions 
  * we also need w values not to be too large since for large values gradients of tanh and sigmoid change very slowly thus slowing down the learning process via gradient descent

* dimensions of weight matrices and biases
  W[layer] = (nodes[layer], nodes[layer - 1])
  B[layer] = (nodes[layer], 1)
  A[layer] = (nodes[layer], num_examples) : activation of layer
