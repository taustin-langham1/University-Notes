

##### Intercept
Intercept (when the value of y = 0) - where the regression line crosses the y-axis
(represents the baseline value of the target variable, when the engine size is zero)
##### Slope
the coefficient of engine size, tells us how much the target variable (CO2 emissions) changes for one-unit increase in the feature
e.g., if the slope is +50, every 1-unit increase in engine size, CO2 emissions increase by 50 units

##### Why are the intercept and slope important in Linear Regression models?

they come together to define the regression line, which is the best-fit line through the data points

equation of the regression line is y = mx + b
(y = dependent variable) - measureD variable
(x = independent variable)
(m = slope) (model.coef_[0])
(b - intercept)(model.intercept_)



##### Performance metrics:

Mean squared Error (MSE) and R^2 Score

##### MSE

- measures the average squared difference between actual values (y) and the predicted values (y with a hat)
- A lower MSE means that the models predictions are closer to the actual values
- MSE is sensitive to large errors because squaring amplifies them
- (the logic behind squaring them means that positive and negative integers don't cancel eachother out)

say you have actual y: 150,200,120
and you have predicted (y with a hat): 155,195,125

MSE = (150-155)^2 + (200-195)^2 + (120-125)^2 **DIVIDED BY** 3 = 25

.... so MSE = 25!!

##### R^2

R Squared measures how well the model explains the variance in the target variable (y). it tells you the proportion of the variance in y that is predictable from the features (x)

![[Pasted image 20250201181205.png]]

SS res = the sum of the squared residuals (errors) = measures how much the models values deviated from the predicted values (predicted values are y with a pointy hat on)
SS tos = the sum of the total squares = measures how much the actual values deviate from their mean (mean is shown as y with a straight line on top)

R^2 compares the model's errors to the errors of a baseline model that always predicts the mean

R^2 ranges from 0 - 1

1 = the model explains all the variance in y (perfect fit)
0 = The model is no better than predicting the mean
< 0 = the model is worse than predicting the mean


so say actual: [150, 200, 120]
and predicted: [155,195,125]

mean (y with a straight line hat on)

= 156.67

![[Pasted image 20250201181730.png]]

##### Why use both?

MSE gives an absolute measure of error, it is useful for comparing models or understanding the magnitude of errors

R^2 gives you a relative measure of how well the model performs compared to baseline (predicting the mean) its useful for understanding the model's explanatory power


