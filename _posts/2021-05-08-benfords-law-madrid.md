---
layout: post
title: "Benford's law and the 2021 Madrid regional election"
date: 2021-05-08
image: /thumbs/madrid-election-thumbnail.jpg
---
I originally wanted the title of this post to be "*Was the 2021 Madrid regional election fraudulent?*", but I found it too much for a post about mathematical calculations and R code.


In particular, this post focuses on [**Bendford's Law**](https://en.wikipedia.org/wiki/Benford%27s_law). This law describes a phenomenon by which, in many real-life collections of numbers, those numbers whose leading digit is 1 will appear more frequently than numbers beginning with other digits. Some examples of these collections of numbers include

1. the number of followers of Twitter users,
2. the number of books in US libraries,
3. the population of Spanish cities,
4. the street numbers of Brazilian addresses, and so on.

In all these collections of numbers the digit that most of the numbers start with is 1, then 2, then 3... and so on, with 9 being the digit that the fewest numbers start with.
The website [testingbenfordslaw.com](testingbenfordslaw.com) provides a visual check of these examples and many more.

![](/img/benford-distribution-450px.png)
*<center><small>The distribution of the first digits, according to Benford's law. Image from Wikipedia.</small></center>*

This law, which might seem not so relevant, has interesting applications in the fields of forensic accounting, auditing and **fraud detection**, as described in the book by M. J. Nigrini, [*Benford's law*](https://books.google.es/books/about/Benford_s_Law.html?id=Bh5Vr_I1NZoC). Among the frauds that are often analyzed with Benford's law are tax fraud and also **electoral fraud**. For example, a claim that circulated on social media after the 2020 US Presidential election was that some of the votes for Joe Biden seemed suspicious because they did not follow Benford's law. The tweet below is an example.

![](/img/twitter-benford-500px.png)
[*<center><small>Tweet by @PetersonAmoriah</small></center>*](https://twitter.com/PetersonAmoriah/status/1333593122861846528)

Last Tuesday (May 4th) there were regional elections in Madrid and I wanted to check whether Benford's law holds true for the results of each municipality in the region. Six main political parties contested the 136 seats in the Madrid Assembly and the results were as follows:
* **Partido Popular**: 65 seats (1,620,213 votes)
* **Más Madrid**: 24 seats (614,660 votes)
* **PSOE**: 24 seats (610,190 votes)
* **Vox**: 13 seats (330,660 votes)
* **Podemos**: 10 seats (261,010 votes)
* **Ciudadanos**: 0 seats (129,216 votes)

The results per municipality and per polling station can be found at [the official site](https://resultados2021.comunidad.madrid/Mesas/es) of the elections. To make things easier though, I have created two CSV files from this data, which can be found in [my GitHub repository](https://github.com/quesadagranja/blog/tree/main/benfords_law). In addition, to analyze the data using Benford's law, I have prepared a very simple piece of code in R that makes use of the [``benford.analysis``](https://search.r-project.org/CRAN/refmans/benford.analysis/html/benford.html) package. The script, which can also be found in my repository, represents a histogram with the leading digits of the electoral results for each municipality of Madrid, and compares it with the ideal curve according to Benford's law. The results are shown below for each of the six main parties:

![](/img/benford-parties.png)
*<center><small>The blue bars show the real distribution of leading digits, whereas the red curve shows the ideal distribution following Benford's law.</small></center>*

As can be seen, **none** of the histograms perfectly meet expectations. The same happens when polling station data is used instead of municipality data. Does this mean that the elections were rigged? I don't think so, because the election result was very close to what most polls predicted weeks ago. So, what's happening here?

The answer may be complex, but it seems that Benford's law is not as good at detecting electoral fraud as it was thought to be. In [a paper](https://www.cambridge.org/core/journals/political-analysis/article/benfords-law-and-the-detection-of-election-fraud/3B1D64E822371C461AF3C61CE91AAF6D) published in 2017, J. Deckert et al. designed a series of simulations to model both fair and fraudulent elections, and they found that "_conformity with and deviations from Benford's law **follow no pattern**_". Indeed, they stated that finding patterns using Benford's law when it comes to elections is similar to "_seeing cats, dogs, and crows in clouds_". So, bookmark this paper for the next time someone proves electoral irregularities using Benford's law!