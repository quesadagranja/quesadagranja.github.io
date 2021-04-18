---
layout: post
title: "pgd: An R package"
date: 2021-04-10
categories: [one, two]
use_math: true
---
I have just released on my GitHub account the first package in R (as far as I know) focused on the **Proper Generalized Decomposition** (PGD). It is called, unsurprisingly, `pgd` (link [here](https://github.com/quesadagranja/pgd "here")), and solves boundary value problems based on the **2D Poisson's equation** in Cartesian coordinates.

## Introduction
This package uses the PGD methodology developed in the article entitled [*A new family of solvers for some classes of multidimensional partial differential equations encountered in kinetic theory modeling of complex fluids*](https://hal.archives-ouvertes.fr/hal-01004909/document), by Amine Ammar et al. This package numerically solves equations of the type

$$\Delta T = - f(x,y)$$

where $$T$$ is a function of $$x$$ and $$y$$ in the domain $$\Omega = \]-M, M\[ \times \]-N, +N\[$$, with homogeneous boundary conditions. The package also includes a plot function to visualize the results.

