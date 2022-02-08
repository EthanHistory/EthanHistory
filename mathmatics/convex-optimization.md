# Convex Optimization

"**Convex optimization** is a subfield of [mathematical optimization](https://en.wikipedia.org/wiki/Mathematical\_optimization) that studies the problem of minimizing [convex functions](https://en.wikipedia.org/wiki/Convex\_function) over [convex sets](https://en.wikipedia.org/wiki/Convex\_set). Many classes of convex optimization problems admit polynomial-time algorithms, whereas mathematical optimization is in general [NP-hard](https://en.wikipedia.org/wiki/NP-hard)"

"A convex optimization problem is an [optimization problem](https://en.wikipedia.org/wiki/Optimization\_problem) in which the objective function is a [convex function](https://en.wikipedia.org/wiki/Convex\_function) and the [feasible set](https://en.wikipedia.org/wiki/Feasible\_region) is a [convex set](https://en.wikipedia.org/wiki/Convex\_set)."



* primary property : **every local minima is a global minima**



{% hint style="info" %}
Why should the feasible set be a convex set as well?

Natural process in my mind keeps telling me convex function would be enough for defining convex optimization. However, it turns out that optimization without a convex set assumption as the feasible set will fall into local minima. the problem doesn't have one of the main properties of convex optimization : "every local minima is a global minima", which means the problem is not a convex optimization problem anymore.

"If we know the solution space is convex, it lets us solve things faster, because we can assume that taking a succession of steps down-slope will lead to the global optimum, without the risk of getting caught in feasibility pockets like we did here."

[https://www.quora.com/In-convex-optimization-why-do-the-set-and-constraints-need-to-be-convex-as-well](https://www.quora.com/In-convex-optimization-why-do-the-set-and-constraints-need-to-be-convex-as-well)

\
TODO : a visual example of non-convex feasible region problem
{% endhint %}

### Convex function

* Definition

"a function is convex if its [epigraph](https://en.wikipedia.org/wiki/Epigraph\_\(mathematics\)) (the set of points on or above the graph of the function) is a [convex set](https://en.wikipedia.org/wiki/Convex\_set)"

{% embed url="https://en.wikipedia.org/wiki/Convex_function" %}

From this conceptual definition, the mathematical definition can be derived by below flow.

First, the definition tell us any convex combination should lie in the epigraph of a function f where 0 <= t <= 1

$$
\forall (x_1, y_1) \:and\:(x_2, y_2) \in epi f, \\
((1-t)x_1 + tx_2, (1-t)y_1+ty_2) \in epi f \\ where\: 0 \leq t \leq 1
$$

By definition of epigraph, you can rewrite above statement as

$$
if \: y_1 \geq f(x_1) \: and \: y_2 \geq f(x_2), then \\
(1-t)y_1 + ty_2 \geq f((1-t)x_1 + tx_2)
$$

Then, you can utilize the premise like below

$$
(1-t) y_1 \geq (1-t)f(x_1) \: and \: ty_2 \geq tf(x_2), \\
(1-t)y_1 + ty_2 \geq (1-t)f(x_1) + tf(x_2)
$$

LHS of the last inequality is the minimum of (1-t)y1 + ty2. Therefore now the definition become more compact form.

$$
(1-t)f(x_1) + tf(x_2) \geq f((1-t)x_1 + tx_2)
$$

* If a function is differentiable, so that you can define the second derivative of that function, there is a convenient way to determine whether the function is convex or not.
  * if the second derivative is non-negative, the function is convex. (inverse also correct)
  * if the second derivative is non-positive, the function is concave. (inverse also correct)



Why the non-negative second derivative makes the function convex?

If you think about the geometrical meaning of the deivative (the slope of the tangent to at the point), the above proposition makes sense to you, drawing few qudratic functions of one variable like Figure 1. For example, if a function have a positive second derivative over any x, the first derivative increase over x. Shortly after, you would imagine a function where the epigraph comes out to be a convex shape like Figure 1.

![Figure 1](<../.gitbook/assets/image\_thumb\[1] (1).png>)

But, for the concise explanation, I posted the proof of the both directions of the proposition.

{% embed url="https://math.stackexchange.com/questions/1224955/proving-that-the-second-derivative-of-a-convex-function-is-nonnegative" %}
convex differentiable function -> non-negative second derivative
{% endembed %}



{% embed url="https://math.ucr.edu/~res/math133/convex-functions.pdf" %}
\[Theorem 2] non-negative second derivative -> convex differentiable function
{% endembed %}

{% file src="../.gitbook/assets/convex-functions.pdf" %}

There is also a convenient way to determine a function is convex.

**a function f(x) is convex iff f''(x) is non-negative**

If you know the geometrical meaning of the deivative (the slope of the tangent to at the point), the above proposition makes sense to you, drawing few qudratic functions of one variable like Figure 1. For example, if a function have a positive second derivative over any x, the first derivative increase over x. Shortly after, you would imagine a function where the epigraph comes out to be a convex shape like Figure 1.

the proof of this proposition in forward direction (the second derivative is non-negative -> convex function) is quite complicate, so I referred an exist proof. &#x20;

### Epigraph

* Definition

$$
epi\:f=\{(x, r)\in X \times \mathbb{R} : r \geq f(x) \}
$$

where, f : X -> R

{% embed url="https://en.wikipedia.org/wiki/Epigraph_(mathematics)" %}



### Feasible Region

"the set of all possible points (sets of values of the choice variables) of an [optimization problem](https://en.wikipedia.org/wiki/Optimization\_problem) that satisfy the problem's [constraints](https://en.wikipedia.org/wiki/Constraint\_\(mathematics\)), potentially including [inequalities](https://en.wikipedia.org/wiki/Inequality\_\(mathematics\)), [equalities](https://en.wikipedia.org/wiki/Equality\_\(mathematics\)), and [integer](https://en.wikipedia.org/wiki/Integer) constraints. This is the initial set of [candidate solutions](https://en.wikipedia.org/wiki/Candidate\_solution) to the problem, before the set of candidates has been narrowed down."

{% embed url="https://en.wikipedia.org/wiki/Feasible_region" %}

