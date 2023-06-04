---
title: "Linear Regression in Machine Learning: A Comprehensive Guide"
seoTitle: "Linear Regression in Machine Learning: A Comprehensive Guide"
seoDescription: "Implement and compare gradient descent linear regression with scikit-learn's LinearRegression, train, predict, and compute MSE"
datePublished: Sun Jun 04 2023 03:30:39 GMT+0000 (Coordinated Universal Time)
cuid: cligv88x100ysa3nv0d7w63e4
slug: linear-regression-in-machine-learning-a-comprehensive-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685680950278/a4b4e0b5-6c00-426a-a55f-5b85825760b9.png
tags: programming, python, machine-learning, python3, python-beginner

---

Machine learning has revolutionized various industries, and one of its key techniques is linear regression. This article provides an in-depth explanation of linear regression, its mathematical foundation, and the gradient descent algorithm. We will also explore the least mean square algorithm, the probabilistic assumptions behind the least-squares cost function, and finally, implement linear regression from scratch using Python and compare it with scikit-learn's implementation. By the end of this article, you will have a solid understanding of linear regression and its practical applications.

You can get all the code here - [Linear Regression and Gradient Descent Code](https://github.com/dotslashbit/blog_notebooks/tree/main/machine_learning/linear_regression)

# Introduction

Let's say we want to predict the price of houses and the following dataset is being used:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685675324207/9b63d015-980a-42c4-9d23-3d4ac133c4ac.png align="center")

* As you know, linear regression is a supervised learning algorithm.
    
* So, there are inputs or features and then there is a label or output.
    
* In the above dataset, the features or inputs are the columns: "Living area (feet^2)" and "#bedrooms" and the label is "Price (1000$s)"
    
* We represent the features as \\(x\\) and the label as \\(y\\).
    
* The \\(x's\\) in this case are two-dimensional vectors in \\(\mathbb{R}^2\\).
    
* For example, \\(x^{(i)}_1\\) represents the living area of the \\(ith\\) house in the training set, while \\(x^{(i)}_2\\)represents the number of bedrooms.
    
* In general, it is up to you to pick which elements to include when building a learning problem, so if you are out in seattle gathering housing data, you might also opt to include other features such as whether each house has a fireplace, the number of bathrooms, and so on. We'll talk more about feature selection later, but for now, just accept the features as they are.
    
* To perform supervised learning, we must first choose how we will represent function/hypotheses in a computer. As this is a linear regression article, suppose we decide to approximate y as a linear function of x:
    

$$h_\theta(x) = \theta_0+\theta_1x_1+\theta_2x_2$$

The \\({\theta_i}'s\\) are the parameters (also known as weights) that parameterize the space of linear functions mapping from \\(X\\) to \\(Y\\). When there is no risk of confusion, we shall remove the subscript \\(\theta\\) in \\(h_\theta(x)\\) and write it as \\(h(x)\\). We also introduce the convention of letting \\(x_0 = 1\\) (this is the intercept term) to simplify our notation.

$$h(x) = \sum_{i=0}^{d}\theta_ix_i=\theta^Tx$$

where \\(\theta\\) and \\(x\\) are both vectors on the right-hand side above, and \\(d\\) is the number of input variables (excluding \\(x_0\\)).

Now, we have the training set but how do we choose or learn the parameters given a training set?

At least for the training examples we have, one viable technique appears to be to make \\(h(x)\\) ( our hypotheses ) close to \\(y\\) ( actual output function ). To formalise this, we will build a function that assesses how near the \\(h(x^{(i)})'s\\) are to the associated \\(y^{(i)}s\\) for each value of the \\(\theta\\)'s. The cost function is defined as follows:

$$J(\theta) = \cfrac{1}{2}\sum_{i=1}^{m}(h_\theta(x^{(i)}) - y^{(i)})^2$$

If you've seen linear regression previously, you might recognise this as the well-known least-squares cost function that underpins the ordinary least squares regression model. Whether or not you've seen it before, let's keep going, and we'll eventually prove that this is a subset of a much larger family of algorithms.

Now, before moving forward let's understand an optimization algorithm known as Gradient Descent Algorithm.

# Gradient Descent Algorithm

* Gradient descent is a widely used optimization algorithm that aims to find the minimum of a function iteratively.
    
* It is commonly employed in machine learning and deep learning for updating the model parameters to minimize the cost function. Here, we will delve into the concepts of gradient descent and visualize its working in both 1D and 2D scenarios using python.
    
* Gradient descent is an iterative optimization algorithm that utilizes the gradient of a function to navigate towards its minimum. It starts with an initial guess of the minimum and updates the guess in the opposite direction of the gradient. The key idea is that by repeatedly taking steps in the direction of the steepest descent, we can eventually converge to a local or global minimum of the function.
    

## 1D Gradient Descent Visualization

* Let's begin by visualizing gradient descent in a 1D scenario.
    
* Consider a simple quadratic function: \\(f(x) = x^2 + 5x + 7\\).
    
* We want to find the value of \\(x\\) that minimizes this function.
    
* By calculating the derivative of the function, we can obtain the gradient, which indicates the direction of the steepest ascent or descent. Using this information, we can iteratively update the value of x until we reach the minimum.
    

The code snippet for 1D gradient descent visualization in Python is as follows:

```python
import numpy as np
import matplotlib.pyplot as plt

def f(x):
    return x ** 2 + 5 * x + 7

def gradient_descent_1d(learning_rate, num_iterations):
    x = -10  # Starting point
    trajectory = [x]
    
    for _ in range(num_iterations):
        gradient = 2 * x + 5  # Gradient of the function
        x = x - learning_rate * gradient
        trajectory.append(x)
    
    return trajectory

learning_rate = 0.1
num_iterations = 20

trajectory = gradient_descent_1d(learning_rate, num_iterations)

x_vals = np.linspace(-15, 5, 100)
y_vals = f(x_vals)

plt.plot(x_vals, y_vals, label='Function')
plt.scatter(trajectory, [f(x) for x in trajectory], color='red', label='Gradient Descent')
plt.xlabel('x')
plt.ylabel('f(x)')
plt.title('1D Gradient Descent')
plt.legend()
plt.grid(True)
plt.show()
```

* In this code, we define the quadratic function `f(x)`, the gradient descent function `gradient_descent_1d`, and the learning rate (`learning_rate`) and number of iterations (`num_iterations`).
    
* We initialize `x` as the starting point and iterate through the specified number of iterations. In each iteration, we calculate the gradient of the function, update the value of `x` using the learning rate, and store the trajectory of `x` in the `trajectory` list.
    
* Finally, we plot the function and the trajectory using Matplotlib.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685627619033/537c0d16-0393-4a6f-bdc1-5b20b3723e2f.png align="center")

You can see how it starts at \\(x=-10\\) and converges to the value of \\(x\\)where \\(f(x)\\)is the smallest.

## 2D Gradient Descent Visualization

Now, let's move on to visualizing gradient descent in a 2D scenario. We will optimize a convex function defined as \\(f(x, y) = x^2 + y^2\\). The principles remain the same as in the 1D case, but now we have two variables to optimize.

The code snippet for 2D gradient descent visualization in Python is as follows:

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import

 Axes3D

def f(x, y):
    return x ** 2 + y ** 2

def gradient_descent_2d(learning_rate, num_iterations):
    x = -5  # Starting point
    y = -5
    trajectory = [(x, y)]
    
    for _ in range(num_iterations):
        grad_x = 2 * x  # Partial derivative with respect to x
        grad_y = 2 * y  # Partial derivative with respect to y
        
        x = x - learning_rate * grad_x
        y = y - learning_rate * grad_y
        
        trajectory.append((x, y))
    
    return trajectory

learning_rate = 0.1
num_iterations = 20

trajectory = gradient_descent_2d(learning_rate, num_iterations)

x_vals = np.linspace(-10, 10, 100)
y_vals = np.linspace(-10, 10, 100)
X, Y = np.meshgrid(x_vals, y_vals)
Z = f(X, Y)

fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.plot_surface(X, Y, Z, cmap='viridis', alpha=0.5)
ax.scatter([x[0] for x in trajectory], [x[1] for x in trajectory], [f(x[0], x[1]) for x in trajectory], color='red', label='Gradient Descent')
ax.set_xlabel('x')
ax.set_ylabel('y')
ax.set_zlabel('f(x, y)')
ax.set_title('2D Gradient Descent')
plt.legend()
plt.grid(True)
plt.show()
```

In this code, we define the convex function `f(x, y)`, the gradient descent function `gradient_descent_2d`, and the learning rate (`learning_rate`) and number of iterations (`num_iterations`). We initialize `x` and `y` as the starting point and iterate through the specified number of iterations. In each iteration, we calculate the partial derivatives with respect to `x` and `y`, update their values using the learning rate, and store the trajectory of `(x, y)` in the `trajectory` list. Finally, we plot the function and the trajectory using Matplotlib's 3D plotting capabilities.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685627780072/37f39fae-c0e9-4446-a34b-852e5fd8ac76.png align="center")

Here, you can see that how it converges, I know it's a bit difficult to see but I hope you get the point.

Now, let's continue our journey of learning linear regression.

# Least Mean Square Algorithm

* We want to select \\(\theta\\) so that \\(J(\theta)\\) is as small as possible because the smaller the cost function \\(J(\theta)\\), the accurate our model will be as the difference between our hypotheses or output function and the actual output will be smaller.
    
* To do this, let's use the gradient descent algorithm that starts with a "initial guess" for \\(\theta\\) and then modifies to make \\(J(\theta)\\) smaller until we ideally converge to a value of that minimises \\(J(\theta)\\).
    
* Consider the gradient descent algorithm, which begins with some initial \\(\theta\\) and conducts the update repeatedly:
    

$$\theta_j := \theta_j - \alpha\cfrac{\partial}{\partial\theta_j}J(\theta)$$

* (This update is executed simultaneously for all values of \\(j = 0,..., d\\).)
    
* The learning rate is referred to as \\(\alpha\\).
    
* As explained above, gradient descent takes a step in the direction of the steepest reduction of \\(J\\) on a regular basis.
    
* To put this procedure into action, we must first determine what the partial derivative term on the right hand side is.
    
* Let's start with the case when we only have one training example \\((x,y)\\), so that we may ignore the sum in the definition of J. We now have:
    

$$\begin{aligned}\cfrac{\partial}{\partial\theta_j}J(\theta) &= \cfrac{\partial}{\partial\theta_j}\cfrac{1}{2}(h_\theta(x)-y)^2 \\ &= 2.\cfrac{1}{2}(h_\theta(x)-y).\cfrac{\partial}{\partial\theta_j}(h_\theta(x)-y) \\ &= (h_\theta(x)-y).\cfrac{\partial}{\partial\theta_j}\left(\sum_{i=0}^{d}\theta_ix_i - y \right) \\ &= (h_\theta(x) - y)x_j \end{aligned}$$

For a single training example, this gives the updated rule:

$$\theta_j \; \colon=\; \theta_j + \alpha(y^{(i)}-h_\theta(x^{(i)}))x_j^{(i)}$$

The Widrow-Hoff learning rule is also known as the LMS update rule (LMS stands for "least mean squares").

This rule has a number of qualities that appear natural and straightforward.

For example, the magnitude of the update is proportional to the error term \\((y^{(i)} - h_\theta(x^{(i)})\\) thus, if we encounter a training example in which our prediction nearly matches the actual value of \\(y^{(i)}\\), there is little need to change the parameters; in contrast, a larger change to the parameters will be made if our prediction \\(h(x^{(i)})\\) has a large error (i.e., if it is very far from \\(y^{(i)}\\)).

When there was only one training example, we developed the LMS rule. There are two approaches to adapt this strategy for a training set with multiple examples. The first is to substitute the following algorithm:

$$\theta_j \; \colon=\; \theta_j + \alpha(y^{(i)}-h_\theta(x^{(i)}))x_j^{(i)} \text{(for every $j$)}\\$$

Repeat the above algorithm till convergence.

By grouping the updates of the coordinates into an update of the vector \\(\theta,\\) we can rewrite the above equation in a slightly more succinct way:

$$\theta \; \colon=\; \theta + \alpha\sum_{i=1}{n}(y^{(i)} - h_\theta(x^{(i)}))x^{(i)}$$

You can readily verify that the quantity in the update rule's summation is just \\(\partial{J(\theta)}/\partial\theta_j\\) (for the original definition of J). As a result, this is just gradient descent on the initial cost function J. This method, known as batch gradient descent, examines every example in the whole training set at each step. While gradient descent is susceptible to local minima in general, the optimisation problem we have posed here for linear regression has only one global and no other local optima; thus, gradient descent always converges to the global minimum (assuming the learning rate is not too high). \\(J\\) is, in fact, a convex quadratic function. Here's an example of gradient descent in action as it attempts to minimise a quadratic function.

%[https://en.wikipedia.org/wiki/File:Gradient_Descent_in_2D.webm] 

![](https://en.wikipedia.org/wiki/File:Gradient_Descent_in_2D.webm align="left")

There's another gradient descent algorithm that works very well and that algorithm is known as Stochastic Gradient Descent. Consider the following algorithm:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685616731073/0d5a846a-8192-49a1-b774-ad24fbd6f7e4.png align="center")

By grouping the updates of the coordinates into an update of the vector \\(\theta\\), we can rewrite the above equation in a slightly more succinct way:

$$\theta\;\colon=\;\theta + \alpha(y^{(i)}-h_\theta(x^{(i)}))x^{(i)}$$

We loop over the training set repeatedly in this algorithm, and each time we find a training example, we change the parameters based on the gradient of the error with regard to that single training example only. This is known as stochastic gradient descent (also known as incremental gradient descent).

Unlike batch gradient descent, which must scan the whole training set before performing a single step—a time-consuming procedure if n is large—stochastic gradient descent can begin making progress immediately and continues to make progress with each example it examines.

Stochastic gradient descent frequently gets "close" to the minimum significantly faster than batch gradient descent. (Note that it may never "converge" to the minimum, and the parameters will continue to oscillate around the minimum of \\(J(\theta)\\); although, in practise, most of the values near the minimum will be relatively close to the genuine minimum.

For these reasons, stochastic gradient descent is frequently chosen over batch gradient descent, especially when the training set is large.

# Why do we choose the least-squares cost function?

Why might linear regression, and specifically the least-squares cost function \\(J\\), be a fair choice when faced with a regression problem? In this part, I will provide a set of probabilistic assumptions that lead to least-squares regression as a highly natural procedure. Assume that the target variables and inputs are linked by the equation:

$$y^{(i)} = \theta^Tx^{(i)} +\epsilon^{(i)}$$

where \\(\epsilon^{(i)}\\) is an error term that represents either unmodeled effects (for example, if there are some variables that are very important in forecasting home prices but were omitted from the regression) or random noise. Assume that the \\(\epsilon^{(i)}\\) are distributed IID (independently and identically distributed) using a Gaussian distribution (also known as a Normal distribution) with mean zero and some variance \\(\sigma^2\\). This assumption can be written as \\(\epsilon^{(i)} \sim \mathcal{N}(0,\sigma^2).\\) In other words, the density of \\(\epsilon^{(i)}\\) is given by

$$p(\epsilon^{(i)})=\cfrac{1}{\sqrt{2\pi\sigma}}exp\left(-\cfrac{(\epsilon^{(i)})^2}{2\sigma^2}\right)$$

This implies that

$$p(y^{(i)}|x^{(i)};\theta) = \cfrac{1}{\sqrt{2\pi\sigma}}exp\left(-\cfrac{(y^{(i)} - \theta^Tx^{(i)})^2}{2\sigma^2}\right)$$

The notation \\(p(y^{(i)}|x^{(i)};\theta)\\) denotes a distribution of \\(y^{(i)}\\) given \\(x^{(i)}\\) and parameterized by \\(\theta\\). We should not condition on \\(p(y^{(i)}|x^{(i)},\theta)\\) because \\(\theta\\) is not a random variable. The distribution of \\(y^{(i)}\\) can also be written as

$$y^{(i)}| x^{(i)};\theta \sim \mathcal{N}(0^Tx^{(i)},\sigma^2)$$

What is the distribution of the \\(y^{(i)}\\)'s given \\(X\\) (the design matrix containing all the \\(x^{(i)}\\)'s and \\(\theta\\). \\(p(\vec{y}|X;\theta)\\) represents the data's probability. For a fixed value of \\(\theta\\), this number is often seen as a function of \\(\vec{y}\\) (and maybe \\(X\\)). When we want to explicitly see this as a function of \\(\theta\\), we'll refer to it as the likelihood function:

$$L(\theta) = L(\theta;X;\vec{y}) = p(\vec{y}|X;\theta)$$

Note that by the independence assumption on the \\(\epsilon^{(i)}\\)'s (and hence also the \\(y^{(i)}\\)’s given the \\(x^{(i)}\\)’s), this can also be written

$$\begin{aligned} L(\theta) &= \prod_{i=1}^{n}p(y^{(i)}|x^{(i)};\theta) \\ &= \prod_{i=1}^{n}\cfrac{1}{\sqrt{2\pi\sigma}}exp\left(-\cfrac{(y^{(i)} - \theta^Tx^{(i)})^2}{2\sigma^2}\right) \end{aligned}$$

Now, given this probabilistic model relating the \\(y^{(i)}\\)’s and the \\(x^{(i)}\\)’s, what is a reasonable way of choosing our best guess of the parameters \\(\theta\\)? The principal of maximum likelihood says that we should choose \\(\theta\\) so as to make the data as high probability as possible. I.e., we should choose \\(\theta\\) to maximize \\(L(\theta)\\).

Instead of maximizing \\(L(\theta)\\), we can also maximize any strictly increasing function of \\(L(\theta)\\). In particular, the derivations will be a bit simpler if we instead maximize the log likelihood \\(l(\theta)\\):

$$\begin{aligned} l(\theta) &= log\;L(\theta) \\ &= log\;\prod_{i=1}^{n}\cfrac{1}{\sqrt{2\pi\sigma}}exp\left(-\cfrac{(y^{(i)} - \theta^Tx^{(i)})^2}{2\sigma^2}\right) \\ &= \sum_{i=1}^{n}log\cfrac{1}{\sqrt{2\pi\sigma}}exp\left(-\cfrac{(y^{(i)} - \theta^Tx^{(i)})^2}{2\sigma^2}\right) \\ &= n\;log\;\cfrac{1}{\sqrt{2\pi\sigma}}-\cfrac{1}{\sigma^2}.\cfrac{1}{2}\sum_{i=1}^{n}(y^{(i)} - \theta^Tx^{(i)})^2 \end{aligned}$$

Hence, maximizing \\(l(\theta)\\) gives the same answer as minimizing

$$\cfrac{1}{2}\sum_{i=1}^{n}(y^{(i)} - \theta^Tx^{(i)})^2$$

which we recognize to be \\(J(\theta)\\), our original least-squares cost function.

Under the previous probabilistic assumptions on the data, least-squares regression corresponds to finding the maximum likelihood estimate of \\(\theta\\). Thus, given one set of assumptions, least-squares regression can be justified as a fairly natural method that just performs maximum likelihood estimation.

It should be noted, however, that the probabilistic assumptions are not required for least-squares to be a perfectly good and reasonable technique; other natural assumptions can be used to support it as well.

Also, in our earlier discussion, our ultimate decision of \\(\theta\\) did not depend on what was \\(\sigma^2\\), and we would have reached the same conclusion even if \\(\sigma^2\\) was unknown. This fact will come up again later when we discuss the exponential family and generalised linear models.

# Implementing Linear Regression from Scratch and with Scikit-Learn

We'll be implementing linear regression algorithm from scratch using python and we'll also see how to use scikit-learning for linear regression.

## Implementing Linear Regression from Scratch

### Importing Libraries

Let's start by importing the necessary libraries

```python
import numpy as np
import matplotlib.pyplot as plt
```

### Generating Synthetic Data To demonstrate the implementation

We will generate some synthetic data. Let's consider a simple dataset with a single independent variable (x) and a dependent variable (y). We will generate 100 data points using a linear equation with some random noise:

```python
np.random.seed(0)  # For reproducibility

# Generate random data
X = np.random.rand(100, 1)
y = 3 + 2 * X + np.random.randn(100, 1) * 0.5
```

### Implementing Linear Regression

Now,we will implement the linear regression algorithm from scratch. The main steps involved are:

* Initializing Parameters: We initialize the slope (beta) and the intercept (alpha) with random values.
    
* Training the Model: We use the ordinary least squares method to estimate the parameters that minimize the sum of squared errors. This involves calculating the gradients and updating the parameters iteratively.
    
* Making Predictions: We use the learned parameters to make predictions on new data.
    

```python
class LinearRegression:
    def __init__(self):
        self.alpha = None  # Intercept
        self.beta = None   # Slope

    def fit(self, X, y):
        X = np.insert(X, 0, 1, axis=1)  # Add a column of ones for the intercept
        XT = X.transpose()
        self.beta = np.linalg.inv(XT.dot(X)).dot(XT).dot(y)
        self.alpha = self.beta[0]
        self.beta = self.beta[1:]

    def predict(self, X):
        X = np.insert(X, 0, 1, axis=1)  # Add a column of ones for the intercept
        return X.dot(np.insert(self.beta, 0, self.alpha))

# Instantiate and fit the model
lr = LinearRegression()
lr.fit(X, y)

# Make predictions
y_pred = lr.predict(X)
```

### Comparing with scikit-learn Linear Regression

Now, let's compare the performance of our custom implementation with scikit-learn's linear regression implementation. We will use scikit-learn's `LinearRegression` class for this purpose.

```python
from sklearn.linear_model import LinearRegression as SKLinearRegression

# Instantiate and fit the scikit-learn model
sk_lr = SKLinearRegression()
sk_lr.fit(X, y)

# Make predictions
sk_y_pred = sk_lr.predict(X)
```

### Visualizing the Data and Fitted Line

To visualize the data and the fitted line, we can use a scatter plot for the data points and a line plot for the fitted line. We will also include the line generated by scikit-learn's implementation for comparison.

```python
# Create subplots
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

# Plot the custom linear regression line
ax1.scatter(X, y, c='b', label='Data')
ax1.plot(X, y_pred, c='r', label='Fitted Line (Custom)')
ax1.set_xlabel('X')
ax1.set_ylabel('y')
ax1.set_title('Custom Linear Regression')
ax1.legend()

# Plot the scikit-learn linear regression line
ax2.scatter(X, y, c='b', label='Data')
ax2.plot(X, sk_y_pred, c='g', label='Fitted Line (scikit-learn)')
ax2.set_xlabel('X')
ax2.set_ylabel('y')
ax2.set_title('scikit-learn Linear Regression')
ax2.legend()

# Adjust layout and display the plot
plt.tight_layout()
plt.show()
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685769637921/d50406e4-5e9b-4b21-95d2-0429990fce95.png align="center")

# Conclusion

In this blog post, we learned the theory behind linear regression, how the optimization works behnig the scenes. We visualized the optimzation algorithm or hte gradient descent algortihm in multiple dimensions.We implemented linear regression from scratch using Python. We compared its performance with scikit-learn's linear regression implementation and visualized the data and fitted lines. The custom implementation provided similar results to the scikit-learn implementation, demonstrating the effectiveness of the algorithm.

By implementing algorithms from scratch, we gain a deeper understanding of the underlying concepts and can customize them to specific needs. However, scikit-learn's implementation offers additional features, optimizations, and integration with other libraries, making it a powerful tool for practical machine learning tasks.

Remember, linear regression is just the tip of the iceberg when it comes to machine learning. Exploring more complex algorithms and techniques will enable you to tackle a wider range of data analysis and prediction problems.