# Activation Functions?

![[Pasted image 20250524190805.png]]


i) 
**RELU**
ReLU(X) = { x ,x > 0
		 { 0, x <= 0	

**EASIER RELU**

**RELU (X) = max(0,x)**

name of function is the Tanh function (as apposed to the sigmoid function)

ii)

**Compute values**

Given x = -2, 0, 2

**ReLU** values:

ReLU(0, -2)
ReLU(0,0)
ReLU(0,2)

0, 0, 2
2?


**THEN TANH**

tanh(−2)=e−2+e2e−2−e2​=0.1353+7.38910.1353−7.3891​=7.5244−7.2538​≈−0.96

done for all is 

-0.96

0

+0.96

e^x - e^-x / e^x + e^-x





iii)

**ReLU** 
- **Limitation**: For negative input values, ReLU outputs zero, which can cause neurons to 'die' or stop learning, if gradients permanently become zero


- **Advantage**: Computationally efficient, sparse activation, reduces vanishing gradient problem of Tanh

**Tanh** 
- **Limitation**: Suffers from the vanishing gradient problem for large inputs, outputs saturate near -1 or 1, causing gradients to shrink and slowing down learning in deep networks  - saturates at large values

- **Advantage**: Better gradient flow than sigmoid 

**Sigmoid**

Outputs 0 - 1
smooth and differentiable

vanishing gradient for large positive/negative inputs
gradients saturate at extreme values


**Hard step**

1 if x > 0 otherwise 0

- simple decision making
- historically used in early perceptrons
no gradient training
not suitable for modern

**Linear Activation Function**  
**Equation**: f(x)=x

**Advantages**:

- Simple, no vanishing gradient.
    
- Useful in output layers for regression tasks.

**Disadvantages**:

- Cannot model complex non-linear patterns.
    
- All layers collapse into a single linear transformation.


# Convolutional Neural Network (CNN)

![[Pasted image 20250524190823.png]]


c is a bunch of 13, so is D 

the classification function is clearly a step function

so its H(x) { 0 x <= 0
		{ 1 x > 0

but i dont know where to go from there, im relatively certain that it cannot be negative or 0, but idk.




iii) In a binary classification task using a Multi-Layer Perceptron (MLP), a neural network
is designed with the following specifications: The network consists of two hidden
layers. The first hidden layer contains 8 neurons, and the second hidden layer consists
of 6 neurons. The input to the network is flattened grayscale images with dimensions
of 28×28 pixels. The output layer consists of a single neuron representing the binary
classification. Each neuron in the network uses a sigmoid activation function. What is
the total number of parameters in this MLP? [2 marks]

a) 6,340
b) 6,287
c) 6,341
d) 6,286

in MLP, each neuron has **Weights, One bias term**

so, **parameters  = weights + bias**

input = 28 * 28 image = 784 input values

first layer: 8 neurons 
second hidden: 6 neurons 
output: 1 neuron 


 28 * 28
 = 784
 
first layer: 784 weights + **1 bias** = 785

785 * 8 = 6280

8 weights + **1 bias** = 9 params

9 * 6 = 54 params

6 weights + **1 bias** = 7 params 
6280 + 54 + 7




The perceptron algorithm is a fundamental building block in neural network models. It
forms the basis of single-layer neural networks and plays a significant role in binary
classification tasks. Consider a binary classification problem where we aim to classify data
samples into two classes (Class 0 and Class 1) based on their features.

i) Explain the perceptron algorithm and its key components, including the perceptron
model, activation function, weight initialization, and the update rule for adjusting the
weights during training. [3 marks]

- The perceptron algorithm is a simple binary classifier. It uses linear model defined by weights and bias to the input features.

- perceptron model: computes weighted sum of input features plus bias
- activation function: applies a function to z to produce an output (in the case of step its between 0 and 1)
- **weights regards perceptron model**: weights wi and bias b are usually initialized to zero or small rundown values
- **update rule (regards weight and bias init)**: during training: for each classified sample, **weights and bias are updated** to reduce classification error


ii) Discuss the limitations of the perceptron algorithm when dealing with non-linearly
separable data and explain why it fails to converge in such cases. Provide examples to
illustrate your explanation. [3 marks]

with the perception linear model, it assumes it can use a straight line or decision boundary to separate classes (linearly seperable) - however when dealing with data which isnt linearly seperable, it fails to adjust to the points  and cannot classify - weights initalise when misclassificaiton occurs, so if classification cannot occur to be analysed then misclassificaiton tjerefore cannot occur therefore the wieghts cant be uipdated

iii) Given a dataset containing two classes of data points that are not linearly separable,
demonstrate how you would modify the perceptron algorithm or incorporate
additional components to improve its performance on the given dataset. [3 marks]


add more hidden layers to the perceptron model - which allows for more complex nonlienar decision boundaries to be established
