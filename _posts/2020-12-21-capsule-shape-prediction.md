---
layout: post
title: Published my article on microcapsule shape prediction!
categories: R&D
img: /img/capsule-levelset-400px.png
---
This week I have a lot to celebrate. One of the articles I wrote three years ago, when I was doing my postdoc at the Université de Technologie de Compiègne (UTC), has been published online! It is entitled [*Real-time prediction of the deformation of microcapsules using Proper Orthogonal Decomposition*](https://www.sciencedirect.com/science/article/pii/S0889974620306629) and can be found in the *Journal of Fluids and Structures*.

A **microcapsule** is a micrometric liquid droplet enclosed by a thin elastic membrane. In nature, they appear in the form of red blood cells, vesicles or eggs. However, they can be artificially created to protect substances inside, such as drugs or aromas, and release them in a controlled way through their rupture. When capsules are suspended in a microfluidic channel, they undergo large deformations, which are tremendously time-consuming to compute. Predicting these deformations is crucial to determine if and when capsules will break.

![](/img/capsule-levelset-400px.png)
*<center>Rendered image of a microcapsule flowing through a channel (not depicted). The color map indicates the distance to the center of the microcapsule.</center>*

Capsule in a microchannel
Image of a capsule flowing through a square-section microchannel from left to right.

In this article we designed a series of strategies to accelerate the calculation of the deformation of microcapsules based on **dimensionality reduction**. In particular, we chose the Proper Orthogonal Decomposition (POD) to obtain the principal components of the shapes of around one hundred deformed capsules from previous simulations. Using the principal components, we obtained a **hypersurface** of solutions as a function of the parameters of the microfluidic channel. In order to *walk* around the hypersurface, and thus predict the shape of the capsule for unknown values of the parameters, we analyzed different approaches.

We found that the **diffuse approximation**, a method developed at UTC similar to the [Locally-Linear Embedding (LLE)](https://en.wikipedia.org/wiki/Nonlinear_dimensionality_reduction#Locally-linear_embedding), provided excellent predictions. As a result, we succeeded in moving from complex simulations that took several days of computation to approximations with minimal error that required only a few seconds. This represents an amazing gain in time of around 8,600,000%!