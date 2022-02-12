---
description: what is the batch size in deep learning and why do we have to care this?
---

# Batch size

{% hint style="info" %}
TODO : Gradient Descent

**the** **first-order iterative optimization algorithm**&#x20;

\
one of the major problem is converge to saddle point
{% endhint %}

{% hint style="info" %}
TODO : Stochastic Gradient Descent (SGD)\
consider only some number of samples (batch) for \
\
(a) convergence to minimizers of strongly-convex functions and to stationary points for non-convex functions (Bottou et al., 2016)\
(b) saddle-point avoidance (Ge et al., 2015; Lee et al., 2016)\
(c) robustness to input data (Hardt et al., 2015)
{% endhint %}

In deep learning, if you know the fundamental reason or not, It is a well-known strategy to properly select batch size because too much batch size cause you to get the model with low generalization power.

However, in common sense, at least my sense, it seems more reasonal to say that you would get a model with better generalization power when you put more data into each iteration. To explain how this impractical-looking phenomenon takes place in practice, I needed to understand how large batch size impact non-convex optimization process.

As a background explanation, let's think about deep learning problem more generally. In the deep learning framework, problems are defined as non-convex optimization and the gradient descent method is commonly used to solve these problems. But the basic gradient descent has a problem with convergence and robustness, therefore they use only a batch size of samples for each parameter update, which is proved to resolve issues in the basic gradient descent.

Here, why large batch size cause the problem with generalization?

the paper that I refered proposes two conjectures with some experiments.

<mark style="color:green;">LB : large batch size, SB : small batch size</mark>

1\) <mark style="color:red;">LB</mark> methods lack the explorative properties of <mark style="color:red;">SB</mark> methods and tend to zoom-in on the minimizer closest to the initial point

2\) <mark style="color:red;">SB</mark> and <mark style="color:red;">LB</mark> methods converge to qualitatively different minimizers with differing generalization properties

> The lack of generalization ability is due to the fact that large-batch methods tend to converge to sharp minimizers of the training function. These minimizers are characterized by a significant number of large positive eigenvalues in ∇2f(x), and tend to generalize less well. In contrast, small-batch methods converge to flat minimizers characterized by having numerous small eigenvalues of ∇2f(x). We have observed that the loss function landscape of deep neural networks is such that large-batch methods are attracted to regions with sharp minimizers and that, unlike small-batch methods, are unable to escape basins of attraction of these minimizers.

Let me make a statement using syllogism to summerize the paper into a short sentense and keep explain one by one.

<mark style="color:blue;">**large batch size -> sharp minimizer -> lower generalization power**</mark>



### Large batch size -> sharp minimizer

Let's start with the first proposition in the statement.

If you use large batch size, there is statistically small difference between the gradient on all the training samples and the gradient on a batch. That means, variance of gradient along the iterations is smaller when you use large batch size. Therefore, in this large batch size regime, it is harder to escape _sharp minimizer_ of _training function_. On the other hand, in the small batch size regime, it is relativly easy to get out the minimizer because some of your batches wouldn't agree to converge to that point due to large variance of gradients along the batches.

![ENTROPY-SGD: BIASING GRADIENT DESCENT INTO WIDE VALLEYS
x-robust is flat minimizer (small batch size)
x-non-robust is sharp minimizer (large batch size)](../.gitbook/assets/캡처.PNG)



### Sharp minimizer -> lower generalization power

I don't know how quantitatively to prove that the model has lower generalization power if the minimizer is sharper, but what we can intuitively understand is that parameters of a model should work on even though there are some small errors in parameters. Robustness or stability with respect to parameters can help to qualitatively understand generalization power. In that sense, it is certain that sharp minimizer where there is a significiant number of large positive eigenvalues ∇2f(x) (hessian of the training function) is very sensitive to parameters and has lower generalization.



### How to overcome sharp minimizer?

Even though the proper batch size is needed, it is hard to know what is the best batch size because it varies in each problem. Fortuneately, there is a interesting experiment in the paper to try to overcome this problem by using hybrid of two regimes. The first step is using small batch size  to find flat-minimizer. After that, you may use large batch size. the paper shows that this hybrid method help to avoid sharp minimizers.



* Reference

{% embed url="https://stats.stackexchange.com/questions/164876/what-is-the-trade-off-between-batch-size-and-number-of-iterations-to-train-a-neu" %}
original discussion
{% endembed %}

{% embed url="https://arxiv.org/pdf/1609.04836.pdf" %}
On Large-Batch Training For Deep Learning: Generalization Gap And Sharp Minima
{% endembed %}
