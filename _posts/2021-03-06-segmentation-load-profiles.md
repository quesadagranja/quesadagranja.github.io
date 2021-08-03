---
layout: post
title: "Segmentation of load profiles by time series feature extraction"
date: 2021-03-06
image: /img/why-segment/thumb.jpg
---               
Part of my current work focuses on the H2020 project entitled [*WHY: Climbing the causality ladder to understand and project the energy demand of the residential sector*](https://www.why-h2020.eu). At University of Deusto, we are building a **causal model** of the energy demand at household level. The objective of this model is to understand, in a quantitative manner, the decision-making process that leads a user to consume electricity and his/her reactions to changes in energy policies.

In order to determine the types of households that exist in terms of energy consumption, a segmentation of [load profiles](https://en.wikipedia.org/wiki/Load_profile) is currently being carried out. Different data sets of household energy load profiles, obtained from public sources, WHY partners, and stakeholders, are being analysed using a methodology based on **time series feature extraction**. First, a set of features that best describe the load profiles (such as statistical moments, quantiles, seasonal aggregates, load factors, entropy, etc.) is selected. Then, these features are computed for the entire data set, creating a feature space that is smaller than the original time series space. Finally, a clustering in the feature space is performed.

Some initial results have been obtained using the *Low Carbon London* data set, publicly available on the [London Datastore website](https://data.london.gov.uk/). This data set contains energy consumption readings for a sample of 5,567 London households, measured between November 2011 and February 2014. A set of features containing aggregated means of different periods (mainly hours, days of the week and months) has been computed, and an unsupervised clustering based on PCA and *k*-means has been performed. The image below shows the average hourly load profiles of two clusters.

![](/img/why-segment/WHY-clusters.png)
*<center><small>Average hourly load profiles of two clusters obtained from the analysis of the Low Carbon London data set.</small></center>*

Although these are just preliminary results, it is already possible to identify different patterns of energy behaviour in the resulting automatic classification (e.g. households with and without a significant electricity consumption in the mornings). These results are therefore very promising, as they show the enormous potential of the proposed methodology for the upcoming analyses.