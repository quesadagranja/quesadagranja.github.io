---
layout: post
title: "Published my second article on microcapsules!"
date: 2021-01-24
categories: [one, two]
---               
A month ago, on Christmas Day, the second (and last) of the articles I wrote during my stay at the Université de Technologie de Compiègne (UTC) was published online. What a cool Christmas present! The article is entitled [*Diffuse approximation for identification of the mechanical properties of microcapsules*](https://journals.sagepub.com/doi/full/10.1177/1081286520977602) and can be found in the journal *Mathematics and Mechanics of Solids*.

As I already mentioned in [my last post](https://quesadagranja.github.io/capsule-shape-prediction), a **microcapsule** is a liquid droplet enclosed by a thin elastic membrane that can be used to release substances in a controlled manner. Microcapsules have a promising future in the field of medicine. Just imagine a medication made up of thousands of these microcapsules filled with drug. By controlling the moment of rupture, it would be possible to release the drug in any target organ!

![](/img/capsule-floating-400px.png)
*<center>Image of a capsule flowing through a square-section microchannel from left to right.</center>*

When microcapsules flow inside a microfluidic channel, they undergo large deformations that modify their shape or even cause their rupture. So it is essential to determine the mechanical properties that define the behavior of microcapsules. In particular, there are three parameters that characterize a microcapsule mechanically: the capsule-to-tube **confinement ratio**, the **capillary number** (which measures the viscosity-to-surface tension ratio), and the **velocity ratio**. The objective of this paper is to determine these three parameters from the shape of a flowing microcapsule observed in a snapshot.

Since the amount of images of flowing capsules labeled with their corresponding parameters was really low (we had just a few), the idea of using convolutional neural networks to perform an automatic identification was initially discarded. Instead, we computed several simulations of microcapsules and measured certain geometric values from them (basically end-to-end distances), as we would have done experimentally. Then, we applied a technique based on **diffuse approximation** to map from the measured geometric values to the required mechanical parameters. As a result, the identification provided low errors over a wide range of values of the estimated parameters! This opens interesting perspectives for applications that require a tight control of the microcapsule mechanical properties.