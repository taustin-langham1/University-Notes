- back propagation
- vanishing / exploding gradients


# Deep Learning

- mlps are shallow
- deep learning stacks many hidden layers
- each layer extracts progressively higher-level features
- this enables complex learning representations

**deep learning cont.**
- hierarchical relationships
- represent complex mappings with fewer parameters
- feature learning => less manual feature engineering

### Deep Learning Challenges

- vanishing / exploding gradients
- initialisation
- variable learning rates / convergence
- Over-fitting
- stopping criteria 
	- relative residual?
- need for lots of data and compute power
- difficult to interpret
- sensitive to hyper-parameters
- can be excessive

### Vanishing/ Exploding gradients

 during back-propagation, gradients are multiplied repeatedly

 very small updates in earlier layers => no learning

small derivatives (<1) shrink exponentially
	no learning!

large derivatives (>1) grow exponentially
	unstable training!

equivalent to high (and increasing) learning rate

**solutions**
- try to maintain gradient flow
	- e.g., ReLU + varients
	- gradient clipping
	- be careful with initializatoin

