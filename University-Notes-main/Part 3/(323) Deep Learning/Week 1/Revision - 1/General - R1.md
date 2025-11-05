
**Perceptrons**
- Hypothesis Functions
- Activations


Using a Perceptron
![[Pasted image 20251028141617.png]]


The weights $\huge w_i$ are given

1. Calculate v = **x * w**
2. Calculate $\huge y=\delta(v)$

But we need $\huge w_i$

We train a perceptron to determine the weights $\huge w_i$

so, in steps:
	1. Initialise weights w, and decide a learning rate $\ell$
	2. for each input x:
		1. Forward propagate to get $v = x \cdot w \;$ and $\; \hat y \;$ and $\; \delta(v)$
		2. calculate the error $\delta = y - \hat y$
		3. Update the parameters, e.g., $\hat w = w + \ell \cdot  \delta \cdot  x$


**example of training a perceptron**

AND Function:

for f(x1, x2) = { True if x1 = x2 = 1, 
			False otherwise

use Binary Step activation function


**Training Perceptron: Example**

- Go through an example



**What are some limitations of a Perceptron?**

Linear Separability (XOR problem, only ever 75% right)
recall how this problem was addressed in decision trees - by adding extra 'branches'

- can also be done in a Perceptron, we can add more layers
- allow more freedom for activation
- can also add more nodes per layer

![[Pasted image 20251028140506.png]]
![[Pasted image 20251028140532.png]]
![[Pasted image 20251028140549.png]]
**How this is worked out**

(Input (3) * L1 (5) )  +  (L1 (5) * L2 (5)) + (L2(5) * L3(4)) + (L3(4) * Output (1))

= (3 x 5) + (5 x 5) + (5 x 4) + (4 x 1)
= 64

