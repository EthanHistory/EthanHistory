# Back propagation



Back propagation is a widely used algorithm for training [feedforward neural networks](https://en.wikipedia.org/wiki/Feedforward\_neural\_network).

Main Idea of this method is on how to calculate influence of each weights toward loss function and using those for gradient descent algorithm.

![](<../.gitbook/assets/스크린샷 2022-02-19 오후 12.53.51.png>)

In the output layer case, it is easy to think of partial derivative y het on J(W) here, because J(W) is contains y het in the activation function. However, In case of weights right after input layer or hidden layers is quite tricky. You can use **chain rules** on this problem. For example, in case of w1, you can break down the partial derivative w1 on J(W) like the above Figure.
