+++
title = "Supervised Learning"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Supervised Learning {#supervised-learning}

**Notations:** <br/>

-   \\(\displaystyle \mathbb{R} :\\)real numbers, \\(\displaystyle \mathbb{R}\_{+} :\\) Positive reals, \\(\displaystyle \mathbb{R}^{d} :\\) d-dimensional vector of reals <br/>

-   \\(\displaystyle x:\\)vector, \\(\displaystyle x\_{j} :j^{th}\\) co-ordinate. \\(\displaystyle \Vert x\Vert :\\) Length of vector \\(\displaystyle x.\\) <br/>

-   \\(\displaystyle x^{1} ,\ x^{2} \ ,x^{3} ,.........,x^{n} :\\) Collection of n vectors. <br/>

-   \\(\displaystyle x\_{j}^{i} :\ j^{th}\\) co-ordinate of \\(\displaystyle i^{th}\\) vector. <br/>

-   \\(\displaystyle ( x\_{1})^{2} :\\) Square fo the first co-ordinate of the vector \\(\displaystyle x\\). <br/>

-   \\(\displaystyle I( 2\ is\ even) \ =\ 1\\). \\(\displaystyle I( 2\ is\ odd) \ =\ 0\\) . <br/>

**Supervised Learning** at its core is simply curve fitting. <br/>

Given \\(\displaystyle \left\\{\left( x^{1} ,y^{1}\right) ,\left( x^{2} ,y^{2}\right) ,\dotsc ,\left( x^{n} ,y^{n}\right)\right\\}\\) find model \\(\displaystyle f\\) such that \\(\displaystyle f\left( x^{i}\right)\\) **close to** \\(\displaystyle y^{i}\\). <br/>


### Regression {#regression}

-   Training data: \\(\displaystyle \left\\{\left( x^{1} ,y^{1}\right) ,\left( x^{2} ,y^{2}\right) ,\dotsc ,\left( x^{n} ,y^{n}\right)\right\\}\\) <br/>

-   \\(\displaystyle x^{i} \in \mathbb{R}^{d} \ ,\ y^{i} \in \mathbb{R} \ \\). <br/>
    (\\(\displaystyle x^{i}\\) would be in a d-dimensional space and \\(\displaystyle y^{i}\\) would be real valued.) <br/>

-   Algoritm outputs a model from \\(\displaystyle f:\mathbb{R}^{d}\rightarrow \mathbb{R}\\). <br/>
    (Learning algo would output a model \\(\displaystyle f\\) which is essentially a functin from \\(\displaystyle \mathbb{R}^{d} \ to\ \mathbb{R}\\)) <br/>

-   Loss \\(\displaystyle [ f]\\) = \\(\displaystyle \frac{1}{n}\sum \_{i=1}^{n}\left( f\left( x^{i}\right) -y^{i}\right)^{2}\\) <br/>
    (Loss of \\(\displaystyle f\\) simply measures the deviation of \\(\displaystyle f\\) of \\(\displaystyle x^{i} \ \\)from \\(\displaystyle y^{i}\\) by a square of things.) <br/>

-   \\(\displaystyle f( x) =\ w^{\top } x+b\ =\ \sum \_{j=1}^{d} w\_{j} x\_{j} +b\\) <br/>

-   Goal of learning algorithms is to find a model with smallest loss possible. <br/>
    (if \\(\displaystyle f\left( x^{i}\right) \ =\ y^{i}\\) for all \\(\displaystyle i\ \\)then that is the samllest loss possible.) <br/>


### Classification {#classification}

-   Training data: \\(\displaystyle \left\\{\left( x^{1} ,y^{1}\right) ,\left( x^{2} ,y^{2}\right) ,\dotsc ,\left( x^{n} ,y^{n}\right)\right\\}\\) <br/>

-   \\(\displaystyle x^{i} \in \mathbb{R}^{d} \ ,\ y^{i} \in \\{+1,−1\\} \ \\) <br/>

-   Algoritm outputs a model from \\(\displaystyle f:\mathbb{R}^{d}\rightarrow \\{+1,−1\\}\\). <br/>
    (Learning algo would output a model \\(\displaystyle f\\) which is essentially a functin from \\(\displaystyle \mathbb{R}^{d} \ to\ \\{+1,−1\\}\\) .) <br/>

-   Loss \\(\displaystyle [ f]\\) = \\(\displaystyle \frac{1}{n}\sum \_{i=1}^{n} 1\left( f\left( x^{i}\right) \neq y^{i}\right)\\) <br/>

-   \\(\displaystyle f( x) =sign\left( \ w^{\top } x+b\ \right)\\) <br/>


### Evaluating Learned Models {#evaluating-learned-models}

-   Learning algorith uses trainig data to get model \\(f\\). <br/>
-   But evaluating the learned model must **not** be done on the trainig data itself. <br/>
-   Use test data that is **not** in the training data for model evaluation <br/>


### Model Selection {#model-selection}

-   Learning algorithms just find the "best" model in the collection of models given by the human. <br/>
-   This is model selection, and it is done by using another subset of data called **validation data** that is distinct from train and test data. <br/>

