- over-fitting, encourage forms of generalisation

- regularisation prevents over-fitting, by adding constraints to the model/trianing

many approaches, but
**common approach**: L(**w**) + $\lambda$R(**w**)

Where:
L(W)  = **LOSS**
$\lambda$ = Trade-off parameter
R(W) = Regularisation

**Types of regularisation:**

Batch normalisation, Penalty Terms
Dropout, Early Stopping
Data Augmentation, Label Smoothing
Noise Injection, Parameter Sharing
Architecture Constraints


**Weight Penalty Regularisation**

- smooth decision boundraries
- introduce a regularisation function R(w) to our loss
- argmin(l(w)+lambdaR(w))