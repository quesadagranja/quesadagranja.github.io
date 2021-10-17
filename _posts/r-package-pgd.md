---
layout: post
title: "An R package for PGD"
date: 2021-04-10
image: /img/pooh/thumb.jpg
---
I just released on my GitHub account the first package in **R** (as far as I know) focused on the [**Proper Generalized Decomposition**](https://en.wikipedia.org/wiki/Proper_generalized_decomposition)! I've unsurprisingly called it `pgd` and can be found [here](https://github.com/quesadagranja/pgd "here"). At the moment it only solves boundary value problems based on the **2D Poisson's equation** in Cartesian coordinates. Depending on its "success", I can consider extending it with other differential equations.

## Introduction
The package implements the methodology developed in the article [*A new family of solvers for some classes of multidimensional partial differential equations encountered in kinetic theory modeling of complex fluids*](https://hal.archives-ouvertes.fr/hal-01004909/document), by Ammar et al., which was the first paper to describe the PGD (although without naming it as such). This package numerically solves two-dimensional Poisson's equations in Cartesian coordinates, that is, equations of the type

$$
\Delta T(x,y) = - f(x,y)
$$

or, equivalently,

$$
\left( \frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2} \right) T(x,y) = -f(x,y)\text{,}
$$

where $T$ is a scalar function of $(x,y)$.

The problem is defined in the rectangular domain

$$
(x,y) \in \Omega = \left(-L_x, +L_x\right) \times \left(-L_y, +L_y \right)
$$

with homogeneous (vanishing) boundary conditions.

The PGD iterative algorithm will seek the solution of the problem in the separate form

$$
T(x,y)= \sum^{\infty}_{j=1} \alpha_j \, F_j(x) \, G_j(y) \text{,}
$$

where functions $F_j(x)$ and $G_j(y)$ are the $j$-th separate components (or *modes*, in the PGD jargon) of the solution. Since the *modes* come in the form of normalized vectors, a coefficient $\alpha_j$ is required to provide the right solution. The number of *modes* generated by the PGD iterative algorithm cannot be known beforehand, but can be controlled by the user.

Due to the separate nature of PGD, the function $f(x,y)$ must also be provided in a separate form.

## Installation
The installation of the ``pgd`` package in your favorite R environment is really easy and can be done in three steps. First, install the ``devtools`` package if you don't have it. To do so, type:

```
{% highlight r %}
install.packages("devtools")
{% endhighlight %}
```

Then, install the ``pgd`` package from my repo:

```
{% highlight r %}
library(devtools)
install_github("quesadagranja/pgd")
{% endhighlight %}
```

Finally, load the package:

```
{% highlight r %}
install.packages("pgd")
{% endhighlight %}
```

That's it!

## Using the package
The package only contains the function ``pgd::poisson_2D()``, which solves the 2D Poisson's equation using PGD. The function has six input arguments, of which three are optional.

The mandatory arguments are:
* The source function ``src``, defined by $f(x,y)$.
* The number of nodes ``n`` to discretize the domain $\Omega$.
* The limits of the mesh ``mlim`` described by $-L_x$, $+L_x$, $-L_y$, $+L_y$.

Since all these arguments are specified for variables $x$ and $y$, lists of the type ``list(x=, y=)`` must be used.

The optional arguments are:
* The nodes ``bc`` of the (vanishing) boundary conditions. The values by default are the first and last nodes.
* The maximum number of iterations ``maxiter``, which must be specified as a list for both the outer loop ``f_iter`` and the inner loop ``r_iter``. The values by default are 500 for ``f_iter`` and 250 for ``r_iter``.
* The error tolerance ``tol``. The outer iteration of the PGD algorithm will stop when the ratio between the last and the first calculated $\alpha$ coefficients is less than this value. The value by default is $10^{-4}$.

The output that the function returns is a list of four components:
* The list of matrices ``f`` with the resulting modes for variables $x$ and $y$.
* The vector ``alpha`` of coefficients.
* The list of coordinates ``coor`` for variables $x$ and $y$.
* The resulting surface ``t``.

Some examples of use are detailed below.

## Examples
The examples shown here are extracted from the paper by [Ammar et al](https://hal.archives-ouvertes.fr/hal-01004909/document) mentioned in the *Introduction* section.

#### Example #1
The first example computes the solution of the 2D Poisson's problem defined in $\Omega = \left(-1, 1\right) \times \left(-1, 1\right)$, with $f(x,y) = \cos(2 \pi x) \sin(2 \pi y)$, assuming that the solution vanishes at the domain boundary. The code to obtain the solution with the ``pgd`` package is shown below.

```
{% highlight r %}
library(pgd)
# Source example
src <- list(
  x = function(x) list(cos(2*pi*x)),
  y = function(y) list(sin(2*pi*y))
)
# Number of nodes
n <- list(
  x = 41,
  y = 41
)
# Mesh limits
mlim <- list(
  x = c(-1, 1),
  y = c(-1, 1)
)
# CALL FUNCTION
o <- pgd::poisson_2D(src, n, mlim)
{% endhighlight %}
```

The variable ``src`` corresponds to the source function $f(x,y)$. Its components must be separated in the list as shown in the example. Separating this function is the most complicated part of the code. If you don't really understand how to do it, pay attention to the other two examples, whose functions are more complex. A grid of $41 \times 41$ nodes is defined in ``n``, and its limits are defined in ``mlim``.

After the execution, the results can be checked in the list ``o``. For example, the $\alpha$ coefficients are

```
{% highlight r %}
> o$alpha
[1] 2.301879e-01 1.804112e-16
{% endhighlight %}
```

This indicates that the solution has been reached in two iterations, although the value of $\alpha_2$ is so low that can perfectly be neglected. The first $x$ and $y$ modes can be represented by typing

```
{% highlight r %}
plot(o$coor$x, o$f$x[,1], type="l", xlab="x", ylab="Fx_1(x)")
plot(o$coor$y, o$f$y[,1], type="l", xlab="y", ylab="Fy_1(y)")
{% endhighlight %}
```

which gives as a result

![](/img/pooh/example1-mode1x.png)

![](/img/pooh/example1-mode1y.png)

The surface of the solution can be plotted by using ``persp`` (only the first three arguments are strictly necessary; the rest are aesthetic extras):

```
{% highlight r %}
persp(
  o$coor$x,
  o$coor$y,
  o$t,
  theta  = -35,
  phi    = 34,
  xlab   = "x",
  ylab   = "y",
  zlab   = "T(x,y)",
  ltheta = -35,
  lphi   = 55,
  shade  = 2.5,
  col    = "darkkhaki"
)
{% endhighlight %}
```

![](/img/pooh/example1-surface.png)

#### Example #2
$$
f(x,y) = x^2 - y^2
$$

```
{% highlight r %} 
src <- list(
  x = function(x) list(x^2, 1),
  y = function(y) list(1, -y^2)
)
{% endhighlight %}
```

#### Example #3
$$
f(x,y) = 2x^2 + x + y^2 - 0.2y + 3xy
$$

```
{% highlight r %} 
src <- list(
  x = function(x) list(2*x^2, x, 1, 1, 3*x),
  y = function(y) list(1, 1, y^2, -0.2*y, y)
)
{% endhighlight %}
```