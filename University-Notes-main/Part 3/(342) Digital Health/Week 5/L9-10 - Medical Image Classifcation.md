## Summary questions:

#### What is Top-n accuracy?

**accuracy (acc) Number of correct images / total test images**

**top-n**
k classes, output = vector k confidence scores corresponding to each k class

in calculating top-n accuracy, if the top-n classes in the result contain the correct class, then this image will be regarded as a correct image in the accuracy calculation

![[Pasted image 20251103102437.png]]


the relationship between top-1 and top-1+n accuracy is that top-1+n will always be greater


#### Describe the linear classifier, and how to train and test it?

$y = Wx + b$

can also be written as

$y = (W,b)$  $\begin{bmatrix}x \\ 1 \end{bmatrix}$


**Training:**
We prepare N training samples (xi, yi), where i = {1,...,N}, yi is the GT class of xi, and yi takes the value in [1,...,K]
then, using the N samples, we train the linear classifier (i.e., learn W and b)

![[Pasted image 20251103103024.png]]