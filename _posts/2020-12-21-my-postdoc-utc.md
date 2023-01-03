---
layout: post
title: "My postdoc at Université de Technologie de Compiègne"
date: 2020-12-21
image: /img/capsule-2/thumb.jpg
---      

In this post, I will share with you the results of the research I conducted during my postdoctoral position at the **Université de Technologie de Compiègne** in France, which took place from January 2017 to July 2018.

My research focused on microcapsules, which are micrometer-sized liquid droplets enclosed by a thin elastic membrane. These microcapsules have potential for use in medicine as controlled drug delivery vehicles. The deformation of microcapsules as they flow through microfluidic channels plays a crucial role in determining their behavior and effectiveness.

In the following three sections, I will present the main findings of the three main studies I published on this topic. These studies are presented in the form of blog posts that I wrote when each of the papers was published.

## Published my article on microcapsule shape prediction!

*This post was published on December 21, 2020*

This week I have a lot to celebrate. One of the articles I wrote three years ago, when I was doing my postdoc at the Université de Technologie de Compiègne (UTC), has been published online! It is entitled [*Real-time prediction of the deformation of microcapsules using Proper Orthogonal Decomposition*](https://www.sciencedirect.com/science/article/pii/S0889974620306629) and can be found in the *Journal of Fluids and Structures*.

A **microcapsule** is a micrometric liquid droplet enclosed by a thin elastic membrane. In nature, they appear in the form of red blood cells, vesicles or eggs. However, they can be artificially created to protect substances inside, such as drugs or aromas, and release them in a controlled way through their rupture. When capsules are suspended in a microfluidic channel, they undergo large deformations, which are tremendously time-consuming to compute. Predicting these deformations is crucial to determine if and when capsules will break.

<center>
<figure>
  <img src="/img/capsule/capsule-levelset-400px.png" alt="Rendered image of a microcapsule flowing through a channel (not depicted). The color map indicates the distance to the center of the microcapsule.">
  <figcaption>Rendered image of a microcapsule flowing through a channel (not depicted). The color map indicates the distance to the center of the microcapsule.</figcaption>
</figure>
</center>

Capsule in a microchannel
Image of a capsule flowing through a square-section microchannel from left to right.

In this article we designed a series of strategies to accelerate the calculation of the deformation of microcapsules based on **dimensionality reduction**. In particular, we chose the Proper Orthogonal Decomposition (POD) to obtain the principal components of the shapes of around one hundred deformed capsules from previous simulations. Using the principal components, we obtained a **hypersurface** of solutions as a function of the parameters of the microfluidic channel. In order to *walk* around the hypersurface, and thus predict the shape of the capsule for unknown values of the parameters, we analyzed different approaches.

We found that the **diffuse approximation**, a method developed at UTC similar to the [Locally-Linear Embedding (LLE)](https://en.wikipedia.org/wiki/Nonlinear_dimensionality_reduction#Locally-linear_embedding), provided excellent predictions. As a result, we succeeded in moving from complex simulations that took several days of computation to approximations with minimal error that required only a few seconds. This represents an amazing gain in time of around 8,600,000%!

## Published my second article on microcapsules!

*This post was published on January 24, 2021*

A month ago, on Christmas Day, the second (and last) of the articles I wrote during my stay at the Université de Technologie de Compiègne (UTC) was published online. What a cool Christmas present! The article is entitled [*Diffuse approximation for identification of the mechanical properties of microcapsules*](https://journals.sagepub.com/doi/full/10.1177/1081286520977602) and can be found in the journal *Mathematics and Mechanics of Solids*.

As I already mentioned in [my last post](https://quesadagranja.github.io/capsule-shape-prediction), a **microcapsule** is a liquid droplet enclosed by a thin elastic membrane that can be used to release substances in a controlled manner. Microcapsules have a promising future in the field of medicine. Just imagine a medication made up of thousands of these microcapsules filled with drug. By controlling the moment of rupture, it would be possible to release the drug in any target organ!

<center>
<figure>
  <img src="/img/capsule-2/capsule-floating-400px.png" alt="Image of a capsule flowing through a square-section microchannel from left to right.">
  <figcaption>Image of a capsule flowing through a square-section microchannel from left to right.</figcaption>
</figure>
</center>

When microcapsules flow inside a microfluidic channel, they undergo large deformations that modify their shape or even cause their rupture. So it is essential to determine the mechanical properties that define the behavior of microcapsules. In particular, there are three parameters that characterize a microcapsule mechanically: the capsule-to-tube **confinement ratio**, the **capillary number** (which measures the viscosity-to-surface tension ratio), and the **velocity ratio**. The objective of this paper is to determine these three parameters from the shape of a flowing microcapsule observed in a snapshot.

Since the amount of images of flowing capsules labeled with their corresponding parameters was really low (we had just a few), the idea of using convolutional neural networks to perform an automatic identification was initially discarded. Instead, we computed several simulations of microcapsules and measured certain geometric values from them (basically end-to-end distances), as we would have done experimentally. Then, we applied a technique based on **diffuse approximation** to map from the measured geometric values to the required mechanical parameters. As a result, the identification provided low errors over a wide range of values of the estimated parameters! This opens interesting perspectives for applications that require a tight control of the microcapsule mechanical properties.

## Published a third article on microcapsules!

*This post was published on September 9, 2021*

The work that I carried out during my stay at the *Université de Technologie de Compiègne*, focused on the dimensionality reduction of a model of microcapsule deformation, continues to bear fruit three years later. The journal *Entropy* has published the paper entitled [*A Data-Driven Space-Time-Parameter Reduced-Order Model with Manifold Learning for Coupled Problems: Application to Deformable Capsules Flowing in Microchannels*](https://www.mdpi.com/1099-4300/23/9/1193/htm), of which I am one of the authors. This is therefore the **third paper on microcapsules** I got published! The paper proposes a dimensionality reduction technique to model **suspensions of microcapsules**, that is, microdrops protected in a thin hyperelastic membrane, which are used in healthcare as drug vehicles.