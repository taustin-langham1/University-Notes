**[Week 6 Slides](file:///C:/Users/langh/Downloads/SCC222-Week6.pdf)**

### So Far:


**VALUE ESTIMATION:** Linear Regression, Logistic Regression

**DATA EXPLORATION:** K-Means Clustering, Hierarchical Clustering

**CLASSIFICATION:** Similarity: KNN, Feature Space Partitioning: Decision Trees & Support Vector Machines, Statistical: Naive Bayes

****

# Decision Trees (Cont.)
**ID3 vs CART**

![[Pasted image 20250221093018.png]]


****
## Overfitting

- Overfitting happens when your model fits too well to the training set
- Overfitting means memorizing 
- Memorizing is not learning 
- it then become difficult for the model to generalize to new examples that were not in the training set
- For example, your model recognizes specific images in your training set instead of general patterns

## Mitigating Overfitting

**Pre-Pruning**
- Set a max depth for the tree to go through
- Minimum number of samples per split
- Minimum reduction in impurity / entropy / MSE
**Post-Pruning**
- carried out once decision tree is built, during cross-validation
- remove nodes that don't improve performance
**Random Decision Forests (RDF's)**
- A random forest is a collection of decision trees whose results are aggregated into one final result
- How to train a Random Decision Forest?
- By training on different samples of the data
- by using a random subset of features

###### **Benefits of pruning**

- Can improve generalization
- Reduces overfitting
- Simplifies the model - more interpretable

## Ensemble Approaches

**Idea**
- Ensemble Approaches combine multiple models to improve performance

**Types of Approach**
- Bootstrap Aggregation: Train same algorithm on different subsets
- Boosting: Sequentially correct errors from previous models

**Aims**
- reduce error and improve accuracy
- build more stable predictions


****

## Decision Trees Regression

training data X, y 
determine first split:
	for each possible threshold compute MSE
	Select the minimum-MSE threshold 
Continue recursively 

## Decision Trees Summary:

- ID3, ENTROPY AND INFORMATION GAIN
- CART, GINI IMPURITY 
- MSE AND REGRESSION
- OVERFITTING AND MITIGATION

****

# Naive Bayes

## Naive Bayes Classifier 

**Probabilistic Classification**

**ASSUMPTION:**

- independence of features / attributes => "Naive"

- E.g.: A fruit may be classified as an apple if its colour is red, its shape is round, and its size approx. 3 inches in diameter

**Classification Problem:**

- given training data containing attributes (A1,...,An) and associated class C
- For sample data, predict the class C given attributes (A1,...,An)

**Key assumption:**
- Each attribute is independent 
**Aim:**
- Learn from the training data 
- Estimate P(C\A1,...An) directly from the data for each class
- Find the class C that maximizes P(C\A1,...An)


## Naive Bayes Theorem:

Bayes Theorem: 

Let A = {A1,...An} be a set of n attributes

Let C denote the associated class.

P(C|A) = P(A|C) * P(C) / P (A)

P(C|A) = What is the chance of event C, given that event A has happened? "Conditional Probability", "Posterior Probability"

P(A|C) = "Likelihood"
P(C) = What is the chance of event C? "Prior Probability"
P(A) "Evidence"

**EXAMPLE**

![[Pasted image 20250221095616.png]]

**Classification Problem:**

- Predict the class C given attributes / features (A1,...,An)
- Each attribute is independent 
- Find the class C that maximizes 
P(C|A1,...,An)
**Aim:**
- Estimate P(C|A1,...,An) directly from the data

**Remember:**

we're looking for the class C* that maximizes probability:

C* = argmax P(C|A)

![[Pasted image 20250221095903.png]]


> So we're comparing P(A|Ci) * P(Ci)

**What if we have multiple attributes?**

if A = {A1,...,An}, how do we compute P(A|Ci)?

i.e., what is P(C|A1,...,An)


Remember: 

1. we assume A1,...,An are independent of each other
2. But C is dependent on each of A1,...An


i.e., P(A1|A2) = P(A1) but P(A|C) != P(A)


// **LOTS OF EXAMPLES AND EXPLAINATIONS YET I REMAIN NAIVE**

## Estimate Probability from Continuous Data

**Discretize the range into bins**

- one ordinal attribute per bin
- Violates independence assumption

**Binary split (A < v) or (A > v)**

- choose only one of the two splits as new attribute

**Probability Density Estimation**

- Assume attribute follows a normal distribution
- Use data to estimate distribution parameters 
- Once distribution known, estimate conditional probability P(Ai|C)


## Probability Density Estimation (Normal Distribution):

- the term "*Bell Curve*" is usually used in the social sciences;
	- in statistics, it's called a **Normal Distribution** and 
	- in physics, it's called a **Gaussian Distribution**
- Many phenomena have probability distributions that are bell curves, including: 
	- Heights, Weights, Exam scores, ect.

- Characteristics of bell curves, normal curves:
	- The mean (average) is always in the center
	- there is only one peak
	- it is symmetric about the mean. Half of data points are to the left of the mean and half are to the right of the mean

![[Pasted image 20250221101123.png]]

> // More fucking examples i don't understand (save me you tube)

## Summary:

**Approach**

- compute the product likelihood and the prior probabilities for each class C
- Assign the class corresponding to the maximum posterior probability

**Robust to isolated noise**

**Can handle missing values**
- ignore the sample during probability estimation calculations

**Independence assumptions may not hold**


