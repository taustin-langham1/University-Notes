**CLASSIFICATION**

supervised classification algorithm


(1) initialization (2) calc distances (3) Sort distances (3) vote on k closest labels to classify






#### How do we choose K?

SQRT(N) / WHERE N IS THE TOTAL NUMBER OF DATA POINTS

K-FOLD - TEST MULTIPLE K VALUES AND CHOOSE THE ONE THAT MINIMISES VALUDATION ERROR

**Small K = Low Bias, High Variance**

low bias makes it closely match the training data
however too closely, meaning high variance (if there's a slight change in the data, the model will react very sensitively to these slight changes)

= **OVERFITTING!**
- overfitting occurs when an algorithm fits too closely or even exactly over its training data
- the model can't make accurate predictions or conclusions from any data other than the training data

**Large K = High Bias, Low Variance**

= **UNDERFITTING !**

- too simple and doesn't capture the underlying relationship

**Bias:** The error introduced by overly simplistic models that cannot capture the underlying data patterns
- high bias: not match data closely
- low bias: closely match data

**Variance:** The error introduced to the models sensitivity to small fluctuations in the training data 




# Accuracy

= TP+TN / TP + TN + FP + FN

or 
CORRECT STUFF  /  EVERYTHING (CORRECT AND INCORRECT STUFF)

### f1 score?

2 x (percison x recall / precision + recall)

precision = TP / TP + FP

recall = TP / TP + FN

recall = false negative one 
precision = false positive one