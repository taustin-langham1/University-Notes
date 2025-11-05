---
cssclasses:
  - '.math-block > mjx-container[jax="CHTML"] { font-size: 2em; }'
---

**Must review this, i wont understand it in one sitting, and with no practice**

**[Week 2 Siles](https://modules.lancaster.ac.uk/mod/resource/view.php?id=2776502)**

Used Math Jax
## Perceptron Limitations

-  limitation to Binary Classification
	- can extend to multi-class with multiple outputs
- No probabilistic output
	- can change the final activation for probabilistic output
- Not Deterministic
	- Depends on solution algorithm
- Linear Separability
	- We can now have non-linear boundaries




$\Huge{v_k^1\,=\,\varphi(\sum_{j=i}^3 w_{j,k}^1 x_j)}$

Combine:

$\Huge{v_{k_4}^4\,=\,\varphi(\sum_{j=i}^4 w_{j_4,k_4}^4 \;\varphi(\sum_{j_4=i}^5 w_{j_3,j_4}^3 (..(..))))}$ 


## Forward Propagation

![[Pasted image 20251014121919.png]]


## Training an MLP


- we aim to minimise the error in the output
- we need a loss function to measure error
- we will use MSE
- where
- ns is the number of samples
- y is the ground truth solution
- y^ is the estimated solution

## Gradient Descent

iterative technique for minimising a function

X^  = X + (small change in X)

$\Huge{\hat X = X + \Delta X}$

start with an initial estimate
find a route to the minimum 
how do we choose the (small change in X)?

## Gradient and Derivatives

- Derivative measures rate of change of a function as its input changes

- if y is a function of x, e.g., y = f(x), then we can write the derivative as

$\frac {dy}{dx'} \; f'(x)$

if 
y = f(x1....xn)

we can consider partial derivatives

dy/dx1, ..., dy/dxn

and the gradient 

change in $f(x) = (\frac {dy}{dx1}, ..., \frac {dy}{dxn})$


## Common Derivatives and Rules

Let 𝛼 ∈ ℂ, 𝑛 ∈ ℤ ≠ 0


- **polynomial rule**: if $f(x) = ax^n$, then $f'(x) = nax^n-1$
![[Pasted image 20251014122830.png]]

example:

$y = x^2$

$dy/dx = 2x$


OR

$y = 3/x^2$

$= 3x^-2$

OR

$\frac {dy}{dx} = -6x^{-3} = \frac{-6}{x^3}$



- **constant**:  $\frac{d}{dx}(a) = 0$

example:

$y = n$   
$\frac{dy}{dx} = 0$  



- **Exp/Log Rules**: Let
- important in activation functions - will show up later

$\huge{f = a^x\qquad \frac {df}{dx} = a^x\; ln\; a}$ 

&

$\huge{g = ln\; x \quad \frac {dg}{dx} = x^{-1}}$

special case:

$\huge{f = e^{x}\;\;\;\frac{df}{dx} = e^x\,ln\,e=e^x}$



- **Trig Rules**


$\frac {d}{dx}(sin\,x) = cos\, x$

$\frac {d}{dx}(cos\,x) = -\,sin\, x$


-  **Linearity**

Example:

$y=2x^2\,+\,3x^{-2}$

so

$\frac{dy}{dx}\,= 4x - 6x^{-3}$

- **Product Rule**
*go over this too*


Example:

$\huge{y = x^ae^x}$

$\huge f' = ax^{a-1}\,,\, g' = e^x$


- **Quotient Rule**

$y = \frac {x^a}{e^x}$
$f = x^a,\;g \;AND\; g'=e^x$
$f' = ax^{a-1}$

$\Huge{\frac{dy}{dx}=\frac{ax^{a-1}e^x-x^ae^x}{(e^x)^2}\;=\;x^{a-1}\frac{a-x}{e^x}}$



**CHAIN RULE**
*most important* - should go over!

![[Pasted image 20251014164819.png]]




## Common Derivatives and Rules - 2

Examples:

**Parameterised sigmoid function is given by:**


$\Huge{f(x) = \frac{1}{1+e^{-\frac{x}{a}}} = (1+e^-{\frac{x}{a})^{-1}}}$


Rewrite as

$\Huge{f(x) = (g(x))^{-1}, g(x)=1+e^{-\frac {x}{a}}}$


![[Pasted image 20251014130647.png]]


##  Back to Gradient Descent


Iterative technique for minimising a function:

$\Huge {\hat x = x + \Delta x}$

Start with an initial estimate 

Find a route to the minimum

Use the negative gradient, e.g.

$\Huge{-\frac{dy}{dx} =-2x}$

Control the amount of movement with "step-size" or "learning rate" $\lambda$

Our update becomes 

$\hat x = x-\lambda \nabla(x)$


Example: Use Gradient descent to minimise

$y = x^2$

initial estimate x = -2.5

learning rate = $\lambda$ = 0.4

gradient = $\frac{dy}{dx} = 2x$

update rule:
$\hat x = x - \lambda \nabla (x)$

## Back to MLP

- we aim to minimise the error in the output
- we need a loss function to measure error
- we will use MSE

$\Huge{L(y, \, \hat y) = \frac {1}{2ns} \sum_{i}^{ns} (yi - \hat yi)^2}$


where ns is the number of samples

y is the ground truth solution

\hat y is the estimated solution

![[Pasted image 20251014133054.png]]

![[Pasted image 20251014133105.png]]