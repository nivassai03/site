+++
title = "Unsupervised Learning"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Unsupervised Learning {#unsupervised-learning}

-   Unsupervised learning is 'understanding data'. <br/>

-   Data: \\(\displaystyle \left\\{x^{1} ,x^{2} ,\dotsc ,x^{n}\right\\}\\) <br/>

-   \\(\displaystyle x^{i} \ \in \mathbb{R}^{d} \ \\) <br/>

-   Build models that compress,explain and group data <br/>


### Dimensionality Reduction {#dimensionality-reduction}

Eg: Represent a million gene expressions levels of a million people,using just 100 numbers per person. <br/>

-   Data: \\(\displaystyle \left\\{x^{1} ,x^{2} ,\dotsc ,x^{n}\right\\}\\) <br/>

-   \\(\displaystyle x^{i} \ \in \mathbb{R}^{d} \ \\) <br/>

-   Encoder: \\(\displaystyle f:\mathbb{R}^{d} \ \rightarrow \mathbb{R}{^{d}}^{'}\\) <br/>
    (always \\(\displaystyle d\ < \ d^{'}\\)) <br/>

-   Decoder \\(\displaystyle f:\ \mathbb{R}{^{d}}^{1}\rightarrow R^{d}\\) <br/>

-   Goal : \\(\displaystyle g\left( f\left( x^{i}\right)\right) \approx x^{i}\\) <br/>

-   Loss = \\(\displaystyle  \frac{1}{n}\sum \_{i=1}^{n} \\| \ g\left( f\left( x^{i}\right)\right) -x^{i} \ \\| ^{2}\\) <br/>


### Density Estimation {#density-estimation}

Eg: Assuming  tweets from an account are independently generated randomly. create a robot account that generate more such tweets. <br/>

To generate such sentences randomly, we need to to be able to assign a probability score to every possible 128 character sentence,giving high scores to those that are likely to be from the original source <br/>

A density estimation model takes in several samples from a random source, and outputs a model that assigns a probability score to every possible instance. <br/>

-   Data: \\(\displaystyle \left\\{x^{1} ,x^{2} ,\dotsc ,x^{n}\right\\}\\) <br/>

-   \\(\displaystyle x^{i} \ \in \mathbb{R}^{d} \ \\) <br/>

-   Probability mapping \\(\displaystyle P:\mathbb{R}^{d}\rightarrow \mathbb{R}\_{+} \ \\)that 'sums' to one. <br/>

-   Goal: \\(\displaystyle P( x)\\) is large if \\(\displaystyle x\ \in \ \\)Data, and low otherwise. <br/>

-   Loss = \\(\displaystyle \frac{1}{n}\sum \_{i=1}^{1}\\)\\(\displaystyle −\log\left( P\left( x^{i}\right)\right)\\) <br/>

