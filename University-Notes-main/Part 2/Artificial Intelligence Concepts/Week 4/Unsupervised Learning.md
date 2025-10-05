
**[Week 4 Slides](file:///C:/Users/langh/Downloads/Week%204%20Lecture%20Slides.pdf)**

- recap: supervised learning
- Unsupervised learning
- K-means clustering 
- Hierarchical Clustering 


# Supervised learning

- use labeled data to train algorithms to predict outcomes and recognize patterns
- similar to a teacher-student scenario

# Unsupervised learning?

- rely on unlabeled data
- learn hidden patterns in the data without human interaction

- the input data is not labeled, output is unknown
- discover patterns, organize the data by similarities, reduce redundancy, extract general rules

### Why unsupervised learning?

- in the reality, not all input data is labeled 
- to find hidden structure of data
- Helpful for finding useful insights from the data

- **unsupervised learning**: Unlabeled data {x} is much cheaper to obtain (100 million unlabeled examples)
- **supervised learning**: Labelled data {{x,y}} is very expensive to obtain (10,000 labeled examples)



### Types of unsupervised learning

- clustering 
	- consists in dividing data into clusters
- Dimensionality
	- Techniques that reduce the number of features, or dimensions, in a dataset
- Association rule mining 
	- Series of algorithms that try to find rules to discover the probability of the co-occurrence of items in a collection
- Anomaly detection 
	- Techniques that discover unusual data points in a data set


### Clustering algorithm

- clustering is the process of dividing the datasets into groups, consisting of similar data points
	- Points in the same group are as similar as possible
	- points in different groups are dissimilar as possible


## K-Means Clustering

- K-Means groups similar points into clusters
- the number of clusters is represented by K
- it is a centroid-based algorithm, where each cluster is associated with a centroid 
- aim: to minimize the sum of distances between the data point and their corresponding cluster centroids 

#### How does K-Means clustering algorithm work?

- Step 1: select the number of clusters you want to identify in your data. this is the "K" in K-means clustering 
- Step 2: Randomly select 3 distinct data points as initial centroids
- Step 3: Measure the distance between 1st point and the three initial centroids
- Step 4: Assign the 1st point to the nearest cluster 
	- Now do the same thing for the next point
	- and the next, repeat until all these points are assigned to the nearest cluster
- Step 5: Calculate the new centroids for each cluster
- Iteration2: Calculate distances again with the new centroids 
- Iteration3: And do it all again

#### K-means - Changing the initialization

- K-means is a heuristic algorithm
	- Different initial centroids may produce different results 


#### Local minima

- k-means is guaranteed to a local minimum, but is not guaranteed to find the global minimum

![[Pasted image 20250207101600.png]]

solution: run multiple times from different random initializations

#### How to choose K?

- **Within-Cluster sum of Squares (WCSS)**: Sum of squared distances between each data point and its assigned cluster centroid

##### The elbow method

- there is a huge reduction in WCSS with K =3, but after that the WCSS doesn't go down as quickly 
- this is called an elbow plot and can pick K by finding the elbow in the plot

![[Pasted image 20250207101914.png]]


### K-Means Summary

- k-means clustering i an optimization problem
- Aim: Minimize the within-cluster sum of squares i.e. variation

- **Strengths**: 
	- Easy to implement
	- Efficiency, time complexity of O(tkn)
- **Weakness**:
	- Local optimum
	- number of cluster
	- non-deterministic
	- clusters of the same size


## Hierarchical Clustering

why hierarchical?
- k-means
	- predetermined number of cluster
	- sensitive to the initial placement of centroids - different results on different runs
	- always try to create the clusters of the same size

- an unsupervised ML algorithm
- to group the unlabeled data into a cluster
- develop the hierarchy of clusters in the form of a tree

### Types of Hierarchical clustering

#### Agglomerative Clustering:
- Bottom-top
- Each observation stats in its own cluster
- Pairs of clusters are merged as you move up the hierarchy


**Step 1**: Create each data point as a single cluster (e.g., 9 data points)
**Step 2**: Take two closest data points or clusters and merge them to form a single cluster, now 8
**Step 3**: Again take the two closest clusters merge them together to form one, now 7
**Step 4:** Repeat step 3 until only one cluster left, once all the clusters are combined, develop the dendrogram to divide the clusters as per problem

#### Divisive Clustering:
- top-bottom
- all observations start in one cluster
- splits are performed recursively as you move down the hierarchy

- a dendrogram is a type of tree diagram showing hierarchical relationships between different sets of data
- dendrogram contains the memory of hierarchical clustering algorithm





![[Pasted image 20250207102825.png]]


![[Pasted image 20250207102842.png]]



## Dimensionality reduction

- **Aim: reduce the number of features or dimensions in a dataset while preserving relationships within the data**

- Simplify data structure -> more efficient algorithms, enable better visualization, and reduce the risk of overfitting in ML models
- Technique: Principal component analysis - PCA

## Association rule mining

- **Aim: Discover interesting relationship patterns between variables in large datasets**

- Identify which items tend to co-occur together in transactions or records. A->B: if item A is purchased, then item B is likely to be purchased

- Apriori algorithm: 1) frequent itemset generation 2) associating rule generation 3) rule pruning 4) rule evaluation 

## Anomaly Detection

- **Aim: detect abnormal patterns in data**


- Three categories of anomalies:
	- Point anomalies: are individual data points that exist far outside the rest of the dataset
	- contextual anomalies: occur when a data point is normal in one context but unusual in another 
	- collective anomalies: a set of data instances that together deviate from the norm, even though individual instances may appear normal

- clustering is a useful tool here as well: anomalies are points that are farthest from any other or points that lie in areas of low density
- applications: intrusion detection, system health monitoring, fraud detection



