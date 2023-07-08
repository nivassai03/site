+++
title = "Machine Learning Foundations"
author = ["John Doe"]
draft = false
weight = 2
toc = true
math = true
+++

## Introduction {#introduction}


### What is Machine Learning {#what-is-machine-learning}

****Definition:**** Machine learning(ML) is the study of computer algorithms that improve automatically through experience and by the use of data. <br/>


#### Task {#task}

-   ****Task**** is something which converts input to an output. <br/>
-   Task can be performed in various levels. <br/>

<!--list-separator-->

-  Task Hierarchy

    {{< figure src="/img/_20230516_231852_20230414_203047screenshot.png" >}} <br/>


#### Why and When Machine Learning? {#why-and-when-machine-learning}

-   When Humans or Programming Fails <br/>
    -   When Scale or Speed or Cost becomes large for human labor <br/>
    -   When we can't express the condition in langugae (ex: Face Detection) <br/>
    -   When we don't know the rules for transforming input to ouput (ex: Weather Prediction). <br/>

<!--listend-->

-   Where Machine Learning can succeed <br/>
    -   Have lots of data relating to the task <br/>
    -   Have some structural idea on the rules <br/>


#### Task Analysis {#task-analysis}

We will analyze the following tasks whether it can be done by human labor or programming or ML. <br/>

**Task - Password Verify** <br/>

-   **Human Labor**:      It doesn't Scale.Verifying every password is impractical. <br/>
-   **Programming**:      It doesn't have any problems in this task. <br/>
-   **Machine Learning**: It doesn't require ML. <br/>

**Task - Face Detection** <br/>

-   **Human Labor**:      It doesn't Scale.Humans checking all faces is impractical. <br/>
-   **Programming**:      We cannot express face in code. <br/>
-   **Machine Learning**: Lots of images are available on internet. <br/>

**Task - Weather Prediction** <br/>

-   **Human Labor**:      Humans doesn't know the rules and can't process much information. <br/>
-   **Programming**:      Cannot code unknown rules. <br/>
-   **Machine Learning**: Lots of weather data available. <br/>


### The Wonder of Machine Learning {#the-wonder-of-machine-learning}

-   Machine Learning is used in your email inbox to filter spam messages. <br/>
-   It is used in e-commerce websites to recommend similar items to that of items in your cart. <br/>
-   Smart Assistans <br/>
-   Robot AIs <br/>
-   Games <br/>
-   Marketing <br/>


## Data, Models and ML Task {#data-models-and-ml-task}


### Data {#data}

**Data** is a collection of vectors. <br/>

{{< figure src="/img/_20230516_232000_20230414_203228screenshot.png" >}} <br/>

**Meatadata** is information on the data. It makes data more readable for humans. <br/>
Example: No of rooms, area in 100 sq.ft, Distance from metro in km, Price in 10 lakhs. (metadata for above data) <br/>


### Model {#model}

**Model** is a mathematical simplification of reality <br/>

Examples: <br/>

-   The Ideal Gas model <br/>
-   Inverse square law for gravitational attraction <br/>
-   Moore's law for semiconductors <br/>
-   Cobb-Douglas model in Economics <br/>

Types of Models: <br/>

-   Predictive Model <br/>
    -   Regression Model <br/>
    -   Classification Model <br/>
-   Probabilistic Model <br/>


#### Predictive Models {#predictive-models}

Their goal is to predict the future outcomes. <br/>

-   **Regression Model:** <br/>
    In regression model we predict continuous vales(the output is a real value). <br/>
    
    Ex: House Prices <br/>
    Model the price of a house based on its area and its distance from metro. <br/>

-   **Classification Model:** <br/>
    In classification model we predict discrete value(which category does the input belongs to). <br/>
    
    Ex: Is it a cat or a dog <br/>
    What class does the image belongs to. <br/>


#### Probabilistic Model {#probabilistic-model}

Their goal is to evaluate how likely a certain event or configuration is. <br/>

Ex: What is the probability that a person belong to certain latitude and longitude. <br/>


### Learning Alogrithm {#learning-alogrithm}

-   A learning alogrithm is what converts data into models. <br/>
-   It chooses a model from a collection of models with same structure and different parameters. <br/>


### Task Hierarchy {#task-hierarchy}

-   Tool is simply the model. <br/>
-   Learning Alogrithms build the right model with guidelines from humans and data. <br/>
    
    {{< figure src="/img/_20230516_232027_20230414_203124screenshot.png" >}} <br/>


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

