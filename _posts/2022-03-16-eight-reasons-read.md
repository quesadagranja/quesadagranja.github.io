---
layout: post
title: "Eight reasons to read the WHY D2.1 Report"
date: 2022-03-16
image: /img/8-reasons/thumb.jpg
---
_This post is an article I wrote for the [WHY Project 3rd Newsletter](https://www.why-h2020.eu/newsletters/third-newsletter/coming-soon-eight-reasons-to-read-d21)._

The D2.1 deliverable, resulting from the work carried out as part of the WHY T2.1, will finally be released for general reading soon. A WHY partner (GOI) and several stakeholders have agreed to share load profile data and disaggregated information (ensuring full compliance with GDPR legislation) feeding into modeling activities. Moreover, several datasets from open data platforms have already been collected and will be added to the data pool. Here are eight good reasons why you can't miss it at all!

**#1**: Because it provides information, at a glance, on twenty load profile datasets from at least eight different countries. Indeed, a summary table has been developed that reports the number of load profiles per dataset, the type of site of the load profiles (whether households, offices, industries, or public administrations), the period of collection of the datasets, the sampling frequency, and even the estimated median length of the load profiles. Adding up the total number of load profiles collected (regardless of their initial length), the value exceeds 55,000!

**#2**: Because it details the 6-step information extraction process that is followed from the selection of a particular dataset until a report of results is produced. These steps are (1) “data extraction”, where we go from arbitrary formats of load profile files to a single format for all; (2) “data cleaning”, where the inaccuracies of load profiles, if any, are corrected; (3) “feature extraction”, where a reduced set of meaningful values is obtained for each load profile that reduce further processing; (4) “cluster analysis”, where load profiles are grouped according to their similar characteristics; (5) “cluster visualization”, which identifies the average load profile within each cluster; and (6) the production of reports depending on the topic being analyzed.

**#3**: Because it details which errors are corrected in the load profiles during the “data cleaning” process, including the imputation of missing values, the adaptation of the load profiles to the local timeframe, and the exclusion of short load profiles (less than one year in duration), to mention a few.

**#4**: Because it explains in great detail which are the more than 3,000 features that are computed per load profile. All features are identified with a unique name, and it is indicated whether the load profiles have to go through a standardization process beforehand. The features are classified by type, the most common type (representing about 90% of the total) being the so-called "seasonal aggregates'', which represent a series of statistical values of the load profiles for certain time slots.

**#5**: Because it explains why 22 of the computed features are named after the title of an American crime novel that became popular in the 1960s.

**#6**: Because all the clustering methods that have been used in the analyses are described, pointing out why most of them have been discarded. In addition, all the validation measures used to determine the most appropriate number of clusters per dataset are also detailed.

**#7**: Because it describes the cluster visualization method used, which is based on the ISO 8601 standard. This method aligns all load profile values to particular times and days of the week, resulting in our iconic heatmaps. Did you know that the ISO 8601 standard considers December 31, 2019 and December 31, 2020 as days of the same 371-day year?

**And #8**: Because all the details of our preliminary analyses are discussed, including (1) the top 40 patterns of electricity consumption, (2) a comparative assessment at regional level of the datasets analyzed, and (3) an assessment of the behavioral changes that occurred before and after the COVID-19 pandemic lockdowns in Spain. Future work and all points with exploitation potential are also provided.

Stay tuned for the release!