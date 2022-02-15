# Perceptron

![](<../.gitbook/assets/캡처 (1).PNG>)

Perceptron is the basic architecture of deep nerual networks (DNN). The first component of it is **"input nodes".** they has one bias or numerical variables on each node as like the inputs in machine learning algorithms. Next, with weights on each input node, you will use **linear combination of inputs and weights**. Finally, the combination will turn into the estimated output in a **"output node"** through one of **non-linear activation functions**.

What I descripbed so far is the process of **forward propagation** in a perceptron, which is the way of inferencing output from input.

> input nodes -> linear combination of input nodes to weights (preactivation) -> applying non-linear activation function (activation) -> output node

It is said that the reason perceptron is designed to use forward propagation is to mimic the mechanism of neruals in our brain. In addition to that, it is also reasonable in the fact that the forward propagation make the back propagation easy to get the gradients efficiently.&#x20;

the nerual network can vary depending on the type of activation function, the number of input nodes, the number of output nodes, the number of weights and perceptron is not enough to understand various types of deep nerual networks. However, this concept of perceptron shows how deep neural networks inference output that we want to predict, classify, estimate.&#x20;
