
Exercise 2: Perceptron and MLP Implementation from Scikit-Learn

why dont things work the first time for me! i think i just want to be dumb


**imports**
```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import Perceptron
from sklearn.datasets import make_classificaiton
from sklearn.neural_network import MLPClassifier
from sklearn.model_selection import train_test_split
from sklearn.mertrics import accuracy_score
```

**E1**
```python

X, y = make_classification(
	n_samples=100,
	n_features=2,
	n_informative=2,
	n_redundant=0,
	n_cluster_per_class=1,
	random_state=0
)

X_train,X_test,y_train,y_test = train_test_split(X,y,test_size=0.2,randomstate=0)



plt.figure()
plt.scatter(X_train[:,0],X_train[:,1],c=y_train)
plt.title("training data")
plt.xlabel("feature1")
plt.ylabel("feature2")
plt.show
plt.figure()
plt.scatter(X_test[:,0],X_test[:,1],c=y_test)
plt.title("testing data")
plt.xlabel("feature1")
plt.ylabel("feature2")
plt.show

```

**perceptron**

```python
perceptron = Perceptron(random_state=0, eta0=0.01)
perceptron.fit(X_train,y_train)
y_pred=perceptron.predict(X_test)
acc = accuracy_score(y_test,y_pred)
print("perceptron accuracy: ", acc)
```

**train and test MLP**

```python
hid_layer(5,)
mlp = MLPClassifier(hidden_layer_sizes=hid_layer, max_iter=1000,random_state=0)
mlp.fit(X_train, y_train)
y_pred_mlp = mlp.predict(X_tst)
print("MLP accuracy:",accuracy_score(y_test,y_pred))
```
