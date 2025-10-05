
**Perceptron can be seen as a simplified model of a biological neuron**

![[Pasted image 20250526123748.png]]

#### Activation Functions - based on differing requirements

- Activation function: A mathematical function applied to a neuron's output in a neural network. it determines whether the neuron "fires" and introduces non-linearity 


![[Pasted image 20250526123605.png]]

- Output range: **0 to 1**
    
- Use case: **Binary classification**, where output represents **probability** of a class (e.g., disease vs. no disease).


![[Pasted image 20250526123612.png]]

- Output range: **–1 to 1**
    
- Use case: Hidden layers in **regression tasks** or when you want centered activations (zero mean), which can help with **training stability and convergence**.



# MLP

stacking multiple layers of perceptron's, we get something that looks like a multi-layer perceptron, which has a stronger expressive capability with multiple hidden layers 


![[Pasted image 20250526124420.png]]



![[Pasted image 20250526125651.png]]



Linear = **OUTPUT** negative infinity to infinity
ReLU = **OUTPUT** 0 to infinity
Step (hard threshold) = **OUTPUT** 0 or 1


**LINEAR**
linear(x) = x // f(x) = x

**RELU**
ReLU(X) = { x ,x > 0
		 { 0, x <= 0	

**STEP**
Step(x) =  { 1 if x>0
		{ 0 otherwise