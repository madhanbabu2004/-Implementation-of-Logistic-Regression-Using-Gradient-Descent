# Implementation-of-Logistic-Regression-Using-Gradient-Descent

## AIM:
To write a program to implement the the Logistic Regression Using Gradient Descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. by using google colab .
2. Upload the dataset .
3. Use the standard libraries in python for finding linear regression.
4. Set variables for assigning dataset values.
5. Import linear regression from sklearn.
7. Predict the values of array.
8. Calculate the accuracy, confusion and classification report by importing the required modules from sklearn. 
9. Obtain the graph

## Program:
```
/*
Program to implement the the Logistic Regression Using Gradient Descent.
Developed by: MADHAN BABU P
RegisterNumber: 212222230075 
*/
```
```
import pandas as pd
df = pd.read_csv('ex2data1 (1).txt')
df

import numpy as np
import matplotlib.pyplot as plt
from scipy import optimize

data = np.loadtxt("ex2data1 (1).txt",delimiter=',')
X = data[:,[0,1]]
y = data[:, 2]

X[:5]

y[:5]

plt.figure()
plt.scatter(X[y == 1][:, 0], X[y == 1][:, 1], label = 'Admitted')
plt.scatter(X[y == 0][:, 0], X[y == 0][:, 1], label = 'Not Admitted')
plt.xlabel("Exam 1 score")
plt.ylabel("Exam 2 score")
plt.legend()
plt.show()

def sigmoid(z):
   return 1 / (1+np.exp(-z))

plt.plot()
X_plot= np.linspace(-10, 10 ,100)
plt.plot(X_plot,sigmoid(X_plot))
plt.show()

def costFunction(theta, X, y):
   h = sigmoid(np.dot(X, theta))
   J = -(np.dot(y, np.log(h)) + np.dot(1-y, np.log(1-h))) / X.shape[0]
   grad = np.dot(X.T, h - y) / X.shape[0]
   return J,grad

X_train = np.hstack((np.ones((X.shape[0], 1)), X))
theta = np.array([0, 0, 0])
J, grad = costFunction(theta, X_train, y)
print(J)
print(grad)

X_train = np.hstack((np.ones((X.shape[0], 1)), X))
theta = np.array([-24, 0.2, 0.2])
J, grad = costFunction(theta, X_train, y)
print(J)
print(grad)

def cost(theta, X, y):
   h = sigmoid(np.dot(X, theta))
   J = -(np.dot(y, np.log(h)) + np.dot(1 - y, np.log(1 - h))) / X.shape[0]
   return J

def gradient(theta, X, y):
   h = sigmoid(np.dot(X, theta))
   grad = np.dot(X.T,h - y) / X.shape[0]
   return grad

X_train = np.hstack((np.ones((X.shape[0], 1)), X))
theta = np.array([0, 0, 0])
res = optimize.minimize(fun = cost, x0 = theta,args=(X_train, y),method = "Newton-CG", jac = gradient)
print(res.fun)
print(res.x)

def plotDecisionBoundary(theta, X, y):
   x_min, x_max = X[:, 0].min() -1 , X[:, 0].max() + 1
   y_min, y_max = X[:, 1].min() - 1, X[:,1].max()+ 1
   xx, yy = np.meshgrid(np.arange(x_min, x_max, 0.1),np.arange(y_min, y_max, 0.1))
   X_plot = np.c_[xx.ravel(), yy.ravel()]
   X_plot = np.hstack((np.ones((X_plot.shape[0], 1)), X_plot))
   y_plot = np.dot(X_plot, theta).reshape(xx.shape)

   plt.figure()
   plt.scatter(X[y == 1][:, 0], X[y == 1][:, 1], label = 'Admitted')
   plt.scatter(X[y == 0][:, 0], X[y == 0][:, 1], label = 'Not Admitted')
   plt.contour(xx, yy, y_plot, levels = [0])
   plt.xlabel("Exam 1 score")
   plt.ylabel("Exam 2 score")
   plt.legend()
   plt.show()

plotDecisionBoundary(res.x, X, y)

prob = sigmoid(np.dot(np.array([1, 45, 85]), res.x))
print(prob)

def predict(theta, X):
  X_train = np.hstack((np.ones((X.shape[0], 1)),X))
  prob = sigmoid(np.dot(X_train, theta))
  return (prob >= 0.5).astype(int)

print('Prediction value of mean:')
np.mean(predict(res.x,x)==y
```



## Output:
# Value of given data set
![output](./a.png)
# Array Value of x
![output](./b.png)
# Array Value of y
![output](./c.png)
# Score graph of exam
![output](./d.png)
# sigmoid function graph
![output](./e.png)
# grade value of x train
![output](./f.png)
# grade value of y train

![output](./g.png)
# res value x
![output](./h.png)
# Decicion boundary for exam
![output](./i.png)
# Proability value
![output](./j.png)
# Prediction value of mean
![output](./k.png)



## Result:
Thus the program to implement the the Logistic Regression Using Gradient Descent is written and verified using python programming.

