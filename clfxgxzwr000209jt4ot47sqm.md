---
title: "NumPy 101: Learn NumPy in 10 minutes"
seoTitle: "NumPy 101 : Learn NumPy in 10 minutes"
seoDescription: "Learn essential numpy operations and functions that can help you write faster and cleaner code."
datePublished: Sat Apr 01 2023 04:23:44 GMT+0000 (Coordinated Universal Time)
cuid: clfxgxzwr000209jt4ot47sqm
slug: numpy-101-learn-numpy-in-10-minutes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680309075185/91f21b2b-9b98-4d2a-b724-75b767984bc9.png
tags: python, data-science, machine-learning, data-analysis, numpy

---

Numpy is a popular Python library for scientific computing and data analysis. It provides a powerful array object, along with many useful functions and methods for manipulating and processing numerical data. In this blog post, I will share some of the essential numpy operations that can help you write faster and cleaner code. Whether you are a beginner or an expert, I hope you will find something useful in this numpy cheat sheet.

# **Installation**

If you don’t have numpy, then first you need to install it. You can install it in two days:

## **Using pip**

```python
pip install numpy
```

## **Using Conda**

First, activate your anaconda environment and then use the following command:

```python
conda install -c anaconda numpy
```

# **The Basics**

Before doing any operations using numpy, we need to import it.

```python
import numpy as np
```

## **Scalar**

Let’s start from the very basic and learn how to create scalar values of numpy class.

```python
# int type

python_int = 2
numpy_int = np.int32(2)
print(type(python_int)) # ---> <class 'int'>
print(type(numpy_int)) # ---> <class 'numpy.int32'>

# float type

python_float = 2.5
numpy_float = np.float32(2.5)
print(type(python_float)) # ---> <class 'float'>
print(type(numpy_float)) # ---> <class 'numpy.float32'>
```

For more detail, take a look at the documentation — [https://numpy.org/doc/stable/reference/arrays.scalars.html#](https://numpy.org/doc/stable/reference/arrays.scalars.html#)

Now, it’s time to move on to Arrays or Lists.

## **1-D Array**

Let’s now create a 1-D array using numpy’s `array()` method.

```python
# creating an 1-D array of int type

one_d_array_int = np.array([1,2,3]) 
print(one_d_array_int) # ---> output : [1 2 3]

# creating an 1-D array of float type

one_d_array_float = np.array([1.5,2.5,3.5])
print(one_d_array_float) # ---> output : [1.5 2.5 3.5]
```

## **2-D Array**

Let’s now create a 2-D array using numpy’s `array()` method.

```python
# 2-D int array

two_d_array_int = np.array([
                [1,2,3],
                [4,5,6],
                [7,8,9]
               ])
print(two_d_array_int) # ---> [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

# 2-D float array

two_d_array_float= np.array([
                [1.1,2.1,3.0],
                [4.1,5.1,6.1],
                [7.1,8.1,9.1]
               ])
print(two_d_array_float) # ---> [[1.1, 2.1, 3.0], [4.1, 5.1, 6.1], [7.1, 8.1, 9.1]]
```

## **Get The Dimension of an Array**

Now, let’s learn how do you get the dimension of the any array.

```python
# If the array is a 1-D array, then it'll return 1
print(one_d_array_int.ndim) # ---> output : 1

# If the array is a 2-D array, then it'l return 2
print(two_d_array_int.ndim) # ---> output : 2
```

## **Get The Shape of an Array**

```python

print(one_d_array_int.shape) # ---> output : (3,)


print(two_d_array_int.shape) # ---> output : (3, 3)
```

As, the `one_d_array_int` is basically a vector, it returns the shape of a vector, whereas `two_d_array_int` is a matrix which has 3 rows and 3 columns and that’s why it returns the shape as (3, 3).

## **Get the Data Type of an Array**

```python
print(one_d_array_int.dtype) # ---> output : dtype('int32')
```

By default, it’s `int32` and there are different size of `int` in numpy that you can use to optimise your space consumption.

## **Manipulating Elements of an Array**

Let’s create a new array and then we will perform operations on this new array.

```python
a = np.array([[1,2,3,4,5,6,7],[8,9,10,11,12,13,14]])
print(a) # ---> output : [[ 1  2  3  4  5  6  7]
#                         [ 8  9 10 11 12 13 14]]
```

## **Access a Specific Element**

Let’s say we want to access first rows’ third element.

```python
# accessing 1st row's 3rd element
print(a[0,2]) # ---> output : 3
```

In numpy to access a specific element then, we first need to specify the **row** and then the **column**.

Remember, numpy also follows the 0-based indexing and due to this if we want to get the first row, we need to write 0 and not 1 and same goes for the column value if we needed the third element, then we’ll write 2 and not 3.

## **Access only a specific row or column**

```python
# accessing only the first row
print(a[0,:]) # ---> output : [1 2 3 4 5 6 7]

# accessing only the second column
print(a[:,1]) # ---> output : [2 9]
```

## **Access elements with skip steps**

```python
# [startindex:endindex:stepsize]
print(a[0, 1:-1:2]) # ---> output : [2 4 6]
```

Here, you are accessing first row’s columns from 2nd column to the last column by accessing every 2nd column.

## **Changing element’s value**

```python
a[0,2] = 99
print(a) # ---> output : [[ 1  2 99  4  5  6  7]
#                         [ 8  9 10 11 12 13 14]]
```

Here, you first assigned the value `99` to the first row’s third column.

# **Special Arrays in Numpy**

## **Zero Matrix**

```python
# creating a zero matrix of shape(2,3)

print(np.zeros((2,3))) # ---> output : [[0. 0. 0.]
 #                                      [0. 0. 0.]
 #                                      [0. 0. 0.]]
```

Here, **2** is the **number of rows** and **3** is the **number of columns.**

## **One Matrix**

```python
# All 1s matrix
print(np.ones((3,2,2))) # ---> output : [[[1. 1.]
#                                        [1. 1.]]
#
#                                        [[1. 1.]
#                                         [1. 1.]]
#                                      
#                                        [[1. 1.]
#                                         [1. 1.]]]

# creating ones matrix int type
print(np.ones((3,2,2)), dtype='int32') # ---> output : [[[1 1]
#                                        [1 1]]
#
#                                        [[1 1]
#                                         [1 1]]
#                                      
#                                        [[1 1]
#                                         [1 1]]]
```

Here, you are creating a matrix of one’s. If you don’t specify any data type then it’ll by default generate float type elements.

## **Random Array**

If you want to have an array having random values of a specific shape, then you can use `np.random.rand()` method.

```python
print(np.random.rand(3,3)) # ---> output : [[0.10671372 0.31133182 0.56572354]
#                                           [0.34792672 0.88867917 0.25310353]
#                                           [0.70052117 0.53243035 0.67948057]]
```

## **Random Array ( Only Integer Values )**

If you want to have an array having random int values of a specific shape, then you can use `np.random.randint()` method.

```python
# np.random.randint(start_value,end_value,size)

print(np.random.randint(-1,5, size=(3,3))) # ---> output : [[0 -1 2]
#                                                           [4 2 1]
#                                                           [4 4 0]]
```

`start_value` is inclusive that’s why -1 is there in the output array.

`end_value` is exclusive that’s why there is no 5 in the output array.

If you don’t mention the `start_value`, then the default start value would be 0. You have to mention the `end_value`.

## **Identity Matrix**

If you want to create an Identiity matrix, then you can use `np.identity()` method.

```python
print(np.identity(3)) # ---> output : [[1. 0. 0.]
#                                      [0. 1. 0.]
#                                      [0. 0. 1.]]
```

You have to mention the `number_of_dimensions`.

## **Transposing Array**

```python
a = np.random.randint(-1,5, size = (2,3)) # creating a random int array
print(a)                                  # output : [[ 2 -1  1]
                                          #           [ 0  1  1]]

print(a.T)                                # output : [[ 2  0]
                                          #           [-1  1]
                                          #           [ 1  1]]
```

## **Reshape Array**

If you want to change the shape of the array you can use `reshape()` method.

```python
a = np.random.randint(-1,5, size = (2,3)) # creating a random int array
print(a)                                  # output : [[ 2 -1  1]
                                          #           [ 0  1  1]]

print(a.reshape(3,2))                     # output : [[ 2  0]
                                          #           [-1  1]
                                          #           [ 1  1]]

print(a.reshape(1,6))                     # output : [[1 2 3 2 2 2]]
```

> *Note : You can’t reshape* `(2,3)` array to `(3,3)` as the original array has `6` cells while the new shape you want to have has `9` cells.

## **Fill with Any Number**

If you want to have an aray filled with a specific value, then you can use `np.full()` method.

```python
print(np.full((3,3), 14)) # ---> output : [[14 14 14]
#                                          [14 14 14]
#                                          [14 14 14]]
```

## **Fill Like**

If you want to have an array with a specific value and you want it to be of same shape as some other array, then you can use `np.full_like()` method.

```python
# Any other number (full_like)
print(np.full_like(a, 4)) # ---> output : [[4 4 4 4 4 4 4]
#                                          [4 4 4 4 4 4 4]]
```

This method takes the shape of the mentioned array and a value, then it creates a new array of the same shape with the given value.

## **Copy Array**

```python
a = [1,2,3]             # created an array a
b = [10,20,30]          # created an array b
print(a)                # output : [1 2 3]
a = b                   # I'll explain it below
b[1] = 200              # changed b's 2nd element's value to 200
print(a)                # output : [10 200 30] HOW??????
```

Let’s first understand what happened here : `a = b`.

Here, the values of `b` didn’t get copied to `a`, instead `a` starts to point to `b` which in-turn changes the values of a but the catch is that whenever you’ll change something in `b` the same will reflect on `a`.

## **Stacking Arrays**

If you want to stack multiple arrays vertically or horizontally, you can use `vstack()` method or `hstack()` method respectively.

```python
# Vertically stacking vectors
v1 = np.array([1,2,3,4])                # created array v1
v2 = np.array([5,6,7,8])                # create array v2

np.vstack([v1,v2,v1,v2])                # output : [[1 2 3 4]
                                        #           [5 6 7 8]
                                        #           [1 2 3 4]
                                        #           [5 6 7 8]]
print(np.hstack([v1,v2]))               # output : [1 2 3 4 5 6 7 8]
```

# **Aggregate Functions**

```python
a = np.array([1, 2, 3])
print(a.sum())                               # sum of all values of a
print(a.max())                               # max of all elements of a
print(a.mean())                              # return mean of a
print(np.median(a))                          # return median of a
print(np.std(a))                             # return standard deviation of a
```

# **Conclusion**

This concludes our numpy cheatsheet blogpost. We hope you found it useful and learned some new tricks to work with arrays and matrices in Python. Numpy is a powerful and versatile library that can help you perform various numerical computations and data analysis tasks. If you want to learn more about numpy, you can check out the official documentation or some of the online tutorials and courses available. Thank you for reading and happy coding!