---
description: Asymptotic Analysis
---

# Analysis of algorithms

## Why _**performance analysis matters in algorithm**_?

Among all the metrics (user friendliness, modularity, security, etc...) where you can assess your algorithms, why every online judge platforms for programming skills mostly cares about performance? Firstly, performance is the most easiest metric to measure either on runtime or asymptotically which I will explain. For example, If you want to measure execution time of a python function, you can just use `time` library. Maybe the measurement can vary depending on the machine where you run the code but relative performance can be checked easily. Furthermore, if you assess your algorithms by asymptotical way, you can check more noticeable differences between your algorithms. Secondly, the fundamental criteria of algorithms is efficiency solving a problem with fully exploiting your knowledge of data structure, algorithms, and so on. Here, programming code is just an expression of your logical flow to solve the problem. In this sense, the best proxy to assess your logical thinking and efficiency of your algorithms would be performance.

## What is Asymptotic analysis?

the most common first method to assess algorithm in any online judge platforms is [Asymptotic analysis](https://en.wikipedia.org/wiki/Asymptotic\_analysis) which is a method to describing limiting behavior of algorithms. Using this method, you can asymptotically assess the performance of your algorithms scaling their input size. In practice, the performance problem stands out when its size is getting bigger and bigger. Therefore, one of the most critical point to be assessed is performance on massive input size. A standard way to do this is asymptotic analysis with big O notation. You just assume some variable input size n and show what other of this n is time complexity of your algorithm. In asymptotic analysis, the actual value n is not important, assuming very bigger value. There are three types of notation used to describe asymptotic bounds of functions (algorithms)

### **Θ Notation**

The first one is theta (Θ) notation. It bounds a function from above and below when the input size becomes enough large.&#x20;

```
Θ(g(n)) = {f(n): there exist positive constants c1, c2 and n0 such 
                 that 0 <= c1*g(n) <= f(n) <= c2*g(n) for all n >= n0}
```

### **Big O Notation**

the second one is very common type used in most of online judge platforms. It only bounds a function from above (defines an upper bound)

```
O(g(n)) = { f(n): there exist positive constants c and 
                  n0 such that 0 <= f(n) <= c*g(n) for 
                  all n >= n0}
```

### **Ω Notation**

As like big O notation, **Ω**(omega) notation defines only an lower bound.

> ```
> Ω (g(n)) = {f(n): there exist positive constants c and
>                   n0 such that 0 <= c*g(n) <= f(n) for
>                   all n >= n0}.
> ```

Almost every algorithms can be categorized below types of algorithm in asymptotic analysis.

* **A logarithmic algorithm – O(logn)** \
  Runtime grows logarithmically in proportion to n.&#x20;
* **A linear algorithm – O(n)** \
  Runtime grows directly in proportion to n.
* **A superlinear algorithm – O(nlogn)** \
  Runtime grows in proportion to n.&#x20;
* **A polynomial algorithm – O(n^c)** \
  Runtime grows quicker than previous all based on n.&#x20;
* **A exponential algorithm – O(c^n)** \
  Runtime grows even faster than polynomial algorithm based on n.&#x20;
* **A factorial algorithm – O(n!)** \
  Runtime grows the fastest and becomes quickly unusable for even \
  small values of n. &#x20;

