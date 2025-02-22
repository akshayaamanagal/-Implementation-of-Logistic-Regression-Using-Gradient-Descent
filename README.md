# Implementation-of-Logistic-Regression-Using-Gradient-Descent

# AIM:
To write a program to implement the the Logistic Regression Using Gradient Descent.

# Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

# Algorithm

1. Import the packages required.
2. Read the dataset.
3. Define X and Y array.
4. Define a function for costFunction,cost and gradient.
5. Define a function to plot the decision boundary and predict the Regression value.

# Program:
```
/*
Program to implement the the Logistic Regression Using Gradient Descent.
Developed by: Akshayaa M
RegisterNumber: 212222230009 
*/

import numpy as np
import matplotlib.pyplot as plt
from scipy import optimize

data = np.loadtxt("ex2data1.txt",delimiter =',')
X= data[:,[0,1]]
y= data[:,2]

X[:5]

y[:5]

plt.figure()
plt.scatter(X[y==1][:,0],X[y==1][:,1],label = "Admitted")
plt.scatter(X[y==0][:,0],X[y==0][:,1],label="Not admitted")
plt.xlabel("Exam 1 score")
plt.ylabel("Exam 2 score")
plt.legend()
plt.show()

def sigmoid(z):
  return 1/(1+np.exp(-z))

plt.plot()
X_plot = np.linspace(-10,10,100)
plt.plot(X_plot, sigmoid(X_plot))
plt.show()

def costFunction(theta,X,y):
  h=sigmoid(np.dot(X,theta))
  J=-(np.dot(y,np.log(h))+ np.dot(1 - y,np.log(1-h))) / X.shape[0]
  grad = np.dot(X.T,h-y)/X.shape[0]
  return J,grad

X_train= np.hstack((np.ones((X.shape[0], 1)),X))
theta=np.array([0,0,0])
J,grad= costFunction(theta,X_train,y)
print(J)
print(grad)

X_train= np.hstack((np.ones((X.shape[0], 1)),X))
theta=np.array([-24,0.2,0.2])
J,grad = costFunction(theta,X_train,y)
print(J)
print(grad)

def cost(theta,X,y):
  h=sigmoid(np.dot(X,theta))
  J= -(np.dot(y,np.log(h))+np.dot(1-y,np.log(1-h)))/X.shape[0]
  return J

def gradient(theta,X,y):
  h=sigmoid(np.dot(X,theta))
  grad=np.dot(X.T,h-y)/X.shape[0]
  return grad

X_train=np.hstack((np.ones((X.shape[0],1)), X))
theta= np.array([0,0,0])
res =optimize.minimize(fun=cost, x0=theta, args=(X_train,y), method='Newton-CG',jac= gradient)
print(res.fun)
print(res.x)

def plotDecisionBoundary(theta,x,y):
  x_min,x_max=x[:,0].min() - 1,x[:,0].max()+1
  y_min,y_max=x[:,1].min() - 1,x[:,1].max()+1
  xx,yy=np.meshgrid(np.arange(x_min,x_max,0.1),np.arange(y_min,y_max,0.1))

  x_plot=np.c_[xx.ravel(),yy.ravel()]
  x_plot=np.hstack((np.ones((x_plot.shape[0],1)),x_plot))
  y_plot=np.dot(x_plot,theta).reshape(xx.shape)

  plt.figure()
  plt.scatter(x[y==1][:,0],x[y==1][:,1],label="Admitted")
  plt.scatter(x[y==0][:,0],x[y==0][:,1],label="Not Admitted")
  plt.contour(xx,yy,y_plot,levels=[0])
  plt.xlabel("Exam 1 score")
  plt.ylabel("Exam 2 score")
  plt.legend()
  plt.show()

plotDecisionBoundary(res.x,X,y)

prob=sigmoid(np.dot(np.array([1,45,85]),res.x))
print(prob)

def predict(theta,X):
  X_train=np.hstack((np.ones((X.shape[0],1)),X))
  prob=sigmoid(np.dot(X_train,theta))
  return (prob>=0.5).astype(int)

np.mean(predict(res.x,X)==y)
```

# Output:
## Array Value of x
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](1.png)
## Array Value of y
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](2.png)
## Exam 1 - score graph
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](3.png)
## Sigmoid function graph
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](4.png)
## X_train_grad value
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](5.png)
## Y_train_grad value
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](6.png)
## Print res.x 
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](7.png)
## Decision boundary - graph for exam score
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](8.png)
## Proability value
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](9.png)
## Prediction value of mean
![Implementation-of-Logistic-Regression-Using-Gradient-Descent](10.png)


# Result:
Thus the program to implement the the Logistic Regression Using Gradient Descent is written and verified using python programming.

