**Linear Regression**:

- Output: Continuous value (e.g., predicting height, price).
    
- Model: y=β0+β1x1+⋯+βnxny = \beta_0 + \beta_1 x_1 + \dots + \beta_n x_ny=β0​+β1​x1​+⋯+βn​xn​.
    
- Error Metric: Mean squared error (MSE), others.
    
- Assumptions: Residuals are normally distributed, homoscedastic, etc.
    
- Use Case: Estimating quantities.
    

**Logistic Regression**:

- Output: Probability between 0 and 1, used for classification.
    
- Model: P(y=1∣x)=11+e−(β0+β1x1+⋯+βnxn)P(y=1|x) = \frac{1}{1 + e^{-(\beta_0 + \beta_1 x_1 + \dots + \beta_n x_n)}}P(y=1∣x)=1+e−(β0​+β1​x1​+⋯+βn​xn​)1​.
    
- Threshold: Probability is thresholded (e.g., > 0.5 ⇒ class 1, else class 0).
    
- Error Metric: Log loss (cross-entropy).
    
- Assumptions: Log-odds of the outcome is a linear function of inputs.
    
- Use Case: Binary or multinomial classification.

## Both

Estimate relationships between values