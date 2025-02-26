**[Week 3 Slides](file:///C:/Users/langh/Downloads/Week%203%20Lecture%20Slides_v2.pdf)**
- Logistic Regression
- K Nearest Neighbors

### Recap: Supervised Learning

- Data has "right answers"
- Learn mappings from an input X to a particular output Y
- Learn from experience to predict new unseen data

 - regression: predict a continuous-valued output
	 - height, price, duration
- Classification: Attempts to separate data into specific categories (or classes or labels)

# Logistic Regression

- Logistic Regression:
	- A classification algorithm
	- used for modelling the probability of a binary outcome based on one or more independent variables
	- Estimate the relationship between the dependent binary variable and independent variables by applying the sigmoid function to ensure that the predicted probabilities lie between 0 and 1

### Logistic Regression vs. Linear Regression

- however, logistic regression is a regression algorithm by nature
- this is because it predicts continuous values ranging from 0 to 1, which is the probability of a class
- Logistic regression = linear regression + sigmoid function

### Regression and Classification

![[Pasted image 20250131100637.png]]

a regression problem becomes a classification problem

- but what is the sigmoid function?

### Sigmoid Function

- It is used to convert continuous values into probabilities for binary classification tasks
- ![[Pasted image 20250131100751.png]]
- It transforms a continuous real number into a value between 0 and 1

### logistic Regression

- logistic regression = linear regression + sigmoid function
- Linear regression: z = wx + b
![[Pasted image 20250131101050.png]]

### Loss function

- the loss function in linear regression is not suitable for logistic regression due to its nonlinearity introduced by the sigmoid function
- ![[Pasted image 20250131101148.png]]

#### Loss function: Logistic Regression

- a suitable loss function in logistic regression is called log-loss
- the purpose of the log-loss is to penalize the model for incorrect probability predictions. the closer the prediction is to the true value, the smaller the loss

![[Pasted image 20250131101355.png]]



Logistic regression is a method used to predict a dependent variable y, given
an independent variable x, such that the dependent variable is categorical
 Consider a binary response:
![[Pasted image 20250131101413.png]]

 Use the sigmoid function to convert the output of a linear regression model
into a probability![[Pasted image 20250131101547.png]]


# K Nearest neighbors


### What is KNN?

- Supervised learning algorithm - Classification
- Classify a new data point based on the majority class of its nearest neighbors


![[Pasted image 20250131101643.png]]



1. Initialization
	- K refers to the number of neighbors
		considered in the algorithm for making
		predictions

2. Calculate distance
➢ Euclidean distance
➢ Squared Euclidean distance
➢ Manhattan distance
➢ Cosine distance

1. Sort Distance
- Sort the nearest neighbors of
the given point by the distances
in increasing order.

1. Vote on labels
- Assign a class label to the new
data point based on the
majority class among its K
nearest neighbors.


### How do we choose K? (1)

- based on feature similarity
	- Choosing the right value of K is a process called parameter tuning, and is important for better accuracy
- Small K: Low Bias, high variance
- Overfitting: 
	- Occurs when an algorithm fits too closely or even exactly to its training data
	- the model cant make accurate predictions or conclusions from any tat other than the training data


#### Bias and Variance

- Bias: the error introduced by overly simplistic models that cannot capture the underlying data patterns
	- high bias: a model with a higher bias would not match the data set closely
	- low bias: a low bias model will closely match the training data set
- Variance: The error introduced due to the models sensitivity to small fluctuations in the training data
	- Low variance: models with high bias will have low variance
	- high variance: models with high variance will have low bias


### How do we choose K? (2)

 Large K: High Bias, Low Variance

 Underfitting:
➢ Underfitting occurs when a model is too simple
➢ It does not capture the underlying relationship
in the training dataset

 As K increases:
➢ Classification boundary becomes smoother
➢ Training error can increase

 Best K controls the balance between
overfitting and underfitting 

#### Methods to choose K

- Sqrt (n), where n is the total number of data points
	- odd value of K is selected to avoid confusion between two classes of data
- K-fold cross-validation : test multiple k values choose the one that minimizes validation error
- split the dataset into k equally-sized folds
- train a model on k-1 fold and validation on the remaining fold
- adapt k based on understanding of the dataset and problem

![[Pasted image 20250131102712.png]]


### Advantages and Disadvantages of KNN

- simple to implement
- robust to the noisy training data
- more effective if the training data is large

- Always needs to determine the value of K which may be complex some time
- the computation cost is high because of calculating the distance between the data points for all the training samples

### Summary - KNN


1. Assign value to K
2. Calculate the distance between the new data point and all other existing data points
3. Sort the distances in ascending order
4. find k nearest neighbors to the new data point based on calculated distances
5. Assign the new data point to the majority class in the nearest neighbors


## Distance Measure

Distance measure will determine the similarity between two elements

![[Pasted image 20250131103152.png]]


### Euclidean distance

- is a measure of the straight-line distance between two points in Euclidean space
- according to the Euclidean distance formula, the distance between two points in the plane with coordinates x,y and a,b is given by:
- ![[Pasted image 20250131103325.png]]

### Squared Euclidean distance

- the SED uses the same equation as the ED, but does not take the square root|
- ![[Pasted image 20250131103422.png]]

### Manhattan distance

- the MD is sum of the absolute difference between coordinates of two points
![[Pasted image 20250131103501.png]]

### Cosine distance

- the cosine distance measures the dissimilarity between two vectors by calculating the cosine of the angle between them in a multi-dimensional space
- it is derived from cosine similarity, which calculates two vectors (words, sentences, features) are similar to each other
- ![[Pasted image 20250131103638.png]]
## Performance Metrics

- Regression metrics:
	- mean squared error
	- mean absolute error
- Classification Metrics
	- Accuracy 
	- precision
	- recall
	- f1 score


### Confusion Matrix

 True Positive (TP): The model correctly predicted a
positive outcome and the actual outcome was positive.
➢ Identify a spam email as spam

 True Negative (TN): The model correctly predicted a
negative outcome and the actual outcome was negative.
➢ Identify a regular email as not spam

 False Positive (FP): The model incorrectly predicted a
positive outcome and the actual outcome was negative.
➢ Identify a regular email as spam

 False Negative (FN): The model incorrectly predicted a
negative outcome and the actual outcome was positive.
➢ Identify a spam as regular email

### Accuracy, Precision, Recall, f1 Score

Accuracy: Accuracy is a measure of how close your estimate is to the actual value

Precision is the proportion of true positive predictions among all instances that
were predicted as positive. It indicates how many of the predicted positive cases
were actually correct.

Recall: is the proportion of true positive instances that were correctly identified by
the model. It reflects the model's ability to detect all actual positive instances.

f1 score: The harmonic mean of precision and recall

![[Pasted image 20250131104009.png]]
