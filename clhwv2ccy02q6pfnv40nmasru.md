---
title: "Mastering Python Function Arguments: A Comprehensive Guide"
seoTitle: "Mastering Python Function Arguments: A Comprehensive Guide"
seoDescription: "Master Python function arguments: comprehensive guide on parameters, positional/keyword arguments, unpacking iterables, and using *args/**kwargs"
datePublished: Sun May 21 2023 03:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clhwv2ccy02q6pfnv40nmasru
slug: mastering-python-function-arguments-a-comprehensive-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684506220781/f5f6bd63-667f-480d-9da8-76a9338abbc2.png
tags: programming-blogs, programming, python, python3, python-beginner

---

Mastering Python function arguments is crucial for any programmer looking to elevate their skills in this versatile language. This comprehensive guide will walk you through the intricacies of parameters and arguments, their differences, and how to effectively use positional and keyword arguments. Additionally, you'll learn about unpacking iterables, leveraging *args and* \*kwargs, and how to bring it all together for cleaner and more efficient code. By the end of this guide, you'll have a solid understanding of Python function arguments and be well-equipped to tackle complex programming tasks.

## Parameters vs Arguments

* Let's say we define a function `my_func(a, b)` and it'll receive two values `a` and `b`.
    
* In this context `a` and `b` are called parameters of `my_func()`.
    
* So, when we define a function, the things that are inside the parentheses are known as parameters.
    
* When we call the function, the things that are inside the parentheses are known as arguments.
    
* So, let's say we created two variables `x = 10` and `y = 'a'`.
    
* Then, we call the `my_func(x, y)` function. Here `x` and `y` are arguments of the function `my_func()`.
    

## Positional and Keyword Arguments

### Positional Arguments

* The most common way of assigning arguments to parameters is via the order in which they are passed i.e. their position.
    
* Suppose, we defined a function `my_func(a, b)` with parameters `a` and `b`.
    
* While calling the function, if we write `my_func(10, 20)`, then 10 will assign to the variable `a` i.e. `a = 10` and 20 will assign to the variable `b` i.e `b = 20`.
    
* If we call the function `my_func(20, 10)`, then 20 will assign to `a` i.e `a = 20` and 10 will assign to `b` i.e `b = 10`.
    

```python
def my_func(a, b, c):
    print("a={0}, b={1}, c={2}".format(a, b, c))

my_func(1, 2, 3)
my_func(2, 1, 3)

# ------------- OUTPUT --------------- #
a=1, b=2, c=3
a=2, b=1, c=3
```

### Default Values

* A positional argument can be made optional by specifying a default value for the corresponding parameter.
    
* Let's say we define a function `my_func(a, b = 10)`, this is how we specify a default value.
    
* So, we are saying if the user/function caller doesn't specify any value for parameter `b`, then set `b = 10`.
    
* We can call this function in two ways:
    
    * `my_func(10, 20)` with this 10 will be assigned to the first parameter i.e. `a` and 20 will be assigned to `b`.
        
    * `my_func(10)` with this 10 will be assigned to the first parameter i.e. `a` and as the user didn't provide the second argument, python will look at the second parameter and assign it the default value that is present in the function definition.
        

```python
def my_func(a, b=10):
    print(f'a={a} and b={b}')

my_func(10)
my_func(10, 20)

# -------------- OUTPUT -------------- #
a=10 and b=10
a=10 and b=20
```

* Suppose we have three parameters and we want to make the second parameter optional.
    
* Let's say we define a function `my_func(a, b = 100, c)` with these three parameters.
    
* So, how would we call this function without specifying a value for the second parameter?
    
* Let's say we call it like this `my_func(10, 20)`.
    
* Is this correct?
    
* I don't think so, let's check.
    
* 10 will be assigned to `a` and 20 will be assigned to..., which one `b` or `c`?
    
* Here, python can't tell which one this value should be assigned to.
    
* In conclusion, if a positional parameter is defined with a default value, then every positional parameter after it must also be given a default value.
    

```python
def my_func(a, b=100, c):
    print(f'a={a} and b={b} and c={c}')

my_func(10, 20)

# ------------- OUTPUT ------------- #
	def my_func(a, b=100, c):
                          ^
SyntaxError: non-default argument follows default argument
```

* So, in the above example, we have to put a default value for `c`.
    
* Let's say we defined a function `my_func(a, b=2, c=3)` with these parameters.
    
* Here, all the following calls are possible:
    
    * `my_func(1)`, here 1 will be assigned to `a`, and for `b` and `c` the respective default values will be assigned.
        
    * `my_func(1,20)`, here 1 will be assigned to `a`, 20 will be assigned to `b` and for `c`, the default value will be assigned.
        
    * `my_func(1,20,30)`, here 1 will be assigned to `a`, 20 will be assigned to `b` and 30 will be assigned to `c`.
        

```python
def my_func(a, b=2, c=3):
    print("a={0}, b={1}, c={2}".format(a, b, c))
    
my_func(1)
my_func(1, 10)
my_func(1, 10, 100)

# ----------------- OUTPUT ---------------- #
a=1, b=2, c=3
a=1, b=10, c=3
a=1, b=10, c=100
```

* But let's say we want to specify the first and the third parameter arguments and take the default value for the second parameter.
    
* Then, how can we do this?
    
* Here, we need the help of keyword arguments.
    

### Keyword Arguments

* To accomplish the above task, you can do this:
    
* `my_func(a=30, c=10)`, by calling this way, you are saying that you want the value for `a` to be 30 and the value for `c` to be 10.
    
* Positional arguments, can **optionally**, be specified using their corresponding parameter name.
    
* This allows us to pass the arguments without sticking to the order of parameters.
    
* Remember, the argument names must be the same as the parameter names.
    
* The following calls are possible:
    
    * `my_func(a=30, c=10)`, by calling this way, you are saying that you want the value for `a` to be 30 and the value for `c` to be 10.
        
    * `my_func(10, c=30)`, by calling this way, you are saying that you want the value for `a` to be 10, the value for `b` should be the default value and the value for `c` should be 30.
        

```python
my_func(a=30, c=10)
my_func(10, c=30)
# ---------------- OUTPUT --------------- #
a=30, b=2, c=10
a=10, b=2, c=30
```

* We can also use keyword arguments even if the function parameter doesn't have any default values.
    
* Let's say we define a function `my_func(a, b, c)`, notice none of the parameters have a default value.
    
* We can call the above function in multiple ways:
    
    * `my_func(1, 2, 3)`
        
    * `my_func(1, 2, c=3)`
        
    * `my_func(a=1, b=2, c=3)`
        
    * `my_func(b=2, a=1, c=3)`
        

```python
def my_func(a, b, c):
    print(f'a={a} and b={b} and c={c}')

my_func(1, 2, 3)
my_func(1, 2, c=3)
my_func(a=1, b=2, c=3)
my_func(b=2, a=1, c=3)

# -------------- OUTPUT ---------------- #
a=1 and b=2 and c=3
a=1 and b=2 and c=3
a=1 and b=2 and c=3
a=1 and b=2 and c=3
```

* In conclusion, by using keyword arguments, you don't need to stick to the order of parameters, you can write them in whichever way you want.
    
* Remember, once you use a named argument, all arguments thereafter must be named too.
    
* Let's say you call the above-defined function like this:
    
    * `my_func(c=1, 2, 4)`, now Python looks at this and it's like okay, 1 is assigned to `c`, but then what, python can't determine which value is for which parameter.
        
* Lastly, using keyword arguments and default arguments, the following calls are possible:
    
    * `my_func(1)`, here 1 will be assigned to `a`, `b` and `c` will be assigned to their respective default values.
        
    * `my_func(a=1, b=2)`, here 1 will be assigned to `a`, 2 will be assigned to `b` and c will get its default value.
        
    * `my_func(c=3, a=1)`, here 3 will be assigned to `c`, 1 will be assigned to `a` and b will get its default value.
        

## Unpacking Iterables

* What defines a tuple in Python, it's not `()`, instead, it's `,`.
    
* `()` is used to make it look clearer.
    
* `1,2,3` is also a tuple.
    
* To create a tuple with a single element, you can do `1,` or `(1,)`.
    
* To create an empty tuple, you can do `tuple()` or `()`.
    

```python
a = (1, 2, 3)
type(a)

# ------------ OUTPUT ------------ #
tuple
```

```python
a = 1, 2, 3
type(a)

# ------------ OUTPUT ------------- #
tuple
```

```python
a = (1,)
type(a)

# --------------- OUTPUT ------------ #
tuple
```

```python
a = 1,
type(a)

# ------------- OUTPUT -------------- #
tuple
```

It won't be a tuple if you removed the `,`.

```python
a = (1)
type(a)

# -------------- OUTPUT ------------- #
int
```

To create an empty tuple, there are two ways:

```python
a = ()
type(a)

# -------------- OUTPUT ------------ #
tuple
```

```python
a = tuple()
type(a)

# ------------- OUTPUT ------------- #
tuple
```

* Packed values refer to values that are bundled together in some way.
    
* Tuples and lists are obvious.
    
* Strings are considered packed values because characters are bundled together.
    
* Sets and dictionaries are also packed values.
    
* A dictionary is a collection of key-value pairs.
    
* Any iterable can be considered a packed value.
    

### Unpacking packed values

* Unpacking is the act of splitting packed values into individual variables contained in a list or tuple.
    
* In other words, you create a tuple or a list that contains variable names and then you unpack the iterable into the variable names.
    
* Let's say you have a list `[1, 2, 3]` and you want to unpack the list into a tuple `a, b, c`.
    
* Remember, there are 3 variables in the list, so we need 3 variables to unpack.
    
* So, the result will be:
    
    * `a` will be 1
        
    * `b` will be 2
        
    * `c` will be 3
        

```python
l = [1, 2, 3, 4]
a, b, c, d = l
print(a, b, c, d)

# ----------- OUTPUT -------------- #
1 2 3 4
```

* Unpacking into individual variables is based on the relative positions of each element.
    
* Unpacking other iterables:
    
    * `a, b, c = 10, 20, 'hello'`
        
    * `a, b, c = 'XYZ'`
        

```python
a, b, c = 'XYZ'
print(a, b, c)

# --------------- OUTPUT ------------- #
X Y Z
```

* You can use this while swapping two values.
    

```python
# traditional way for swapping two variables
a = 10
b = 20
print("a={0}, b={1}".format(a, b))

tmp = a
a = b
b = tmp
print("a={0}, b={1}".format(a, b))

# ---------------- OUTPUT -------------- #
a=10, b=20
a=20, b=10
```

```python
# using unpacking
a = 10
b = 20
print("a={0}, b={1}".format(a, b))

a, b = b, a
print("a={0}, b={1}".format(a, b))

# ---------------- OUTPUT --------------- #
a=10, b=20
a=20, b=10
```

* While unpacking dictionaries:
    
    * let's say we have a dictionary `d = {'key1': 1, 'key2': 2, 'key3': 3}`
        
    * Then, if we write `a, b, c = d`, we will get the keys of the dictionary and not the values.
        

```python
dict1 = {'p': 1, 'y': 2, 't': 3, 'h': 4, 'o': 5, 'n': 6}
dict1
a, b, c, d, e, f = dict1
print(a)
print(b)
print(c)
print(d)
print(e)
print(f)

# ------------ OUTPUT ------------ #
p
y
t
h
o
n
```

Note: Python Dictionary is ordered after Python 3.6 but sets are still unordered.

* Here, `a` will be `key1`, `b` will be `key2` and `c` will be `key3`.
    
* While using sets:
    
    * let's say we have a set `s = {'h', 'e', 'l', 'l', 'o'}`
        
    * If we unpack we can get different answers this is also an unordered type.
        

```python
s = {'p', 'y', 't', 'h', 'o', 'n'}
print(s)
a, b, c, d, e, f = s

# ----------- OUTPUT ----------------- #
{'t', 'h', 'n', 'o', 'p', 'y'}
p
t
y
n
o
h
```

## Extended Unpacking(\* and \*\* )

### Use case for \*

* We always don't want to unpack every single element in an iterable.
    
* We may, for example, want to unpack the first value, and then unpack the remaining values into another variable.
    
* Let's say we have a list `l = [1, 2, 3, 4, 5, 6]`.
    
* We can achieve our goal in multiple ways:
    
    * Using slicing:
        
        * You can do `a = l[0]` and `b = l[1:]`.
            
    * Using simple unpacking:
        
        * `a, b = l[0], l[1:]`
            
    * Using \* operator:
        
        * `a, *b = l`
            

```python
l = [1, 2, 3, 4, 5, 6]
# using slicing
a = l[0]
b = l[1:]
print(a)
print(b)

# ---------- OUTPUT -------------- #
1
[2, 3, 4, 5, 6]
```

```python
# using unpacking 
a, b = l[0], l[1:]
print(a)
print(b)

# ----------- OUTPUT ------------- #
1
[2, 3, 4, 5, 6]
```

```python
# using * operator
a, *b = l
print(a)
print(b)

# ----------- OUTPUT ------------- #
1
[2, 3, 4, 5, 6]
```

Let's see another example with tuples

```python
a, *b = -10, 5, 2, 100
print(a)
print(b)

# ------------ OUTPUT ------------ #
-10
[5, 2, 100]
```

Let's take another example with strings

```python
a, *b = 'python'
print(a)
print(b)

# ------------ OUTPUT ----------- #
p
['y', 't', 'h', 'o', 'n']
```

What about extracting the first, second, last and the rest elements?

```python
# with slicing
s = 'python'

a, b, c, d = s[0], s[1], s[2:-1], s[-1]
print(a)
print(b)
print(c)
print(d)

# ------------- OUTPUT ------------ #
p
y
tho
n
```

```python
# with unpacking
a, b, *c, d = s
print(a)
print(b)
print(c)
print(d)

# ---------- OUTPUT ----------- #
p
y
['t', 'h', 'o']
n
```

Here, `c` is a list of characters and not a string, if that's a problem then you can use the `join()` function to get the string from list.

#### Usage with Ordered Types

* `a, *b = [1, 2, 3, 4]`, then `a = 1` and `b = [2, 3, 4]`
    
* `a, *b = (10, 20, 30, 40)`, then `a = 10` and `b = [20, 30, 40]` (notice we always get a list type after unpacking).
    
* `a, *b = 'XYZ'`, then `a = 'X'` and `b = ['Y', 'Z']`.
    
* `a, b, *c = 1, 2, 3, 4, 5`, then `a = 1`, `b = 2`, and `c = [3, 4, 5]`.
    
* `a, b, *c, d = 1, 2, 3, 4, 5, 6`, then `a = 1`, `b = 2`, `c = [3, 4]`, and `d = 5`.
    
* `a, *b, c, d = 'python'`, then `a = 'p'`, `b = ['y', 't', 'h']`, `c = 'o'` and `d = 'n'`.
    
* `a, *b = {'p':1, 'y': 2, 't': 3, 'h': 4, 'o': 5, 'n': 6}`, then `a='p'` and `b = ['y', 't', 'h', 'o', 'n']`.
    
* We can't get key-value pairs by unpacking from RHS, but we can get key-value pairs while unpacking from LHS.
    
* Till now, we have seen that we can unpack from RHS, but we can also unpack from LHS.
    
* Let's say we have `l1 = [1, 2, 3]` and `l2 = [4, 5, 6]`.
    
* Then to unpack this we can write `l = [*l1, *l2]`
    
* This will result in `l = [1,2,3,4,5,6]`.
    
* As you can see this unpacks the two lists into individual elements.
    
* Let's take another example with dictionaries.
    

```python
d1 = {'key1': 1, 'key2': 2}
d2 = {'key2': 3, 'key3': 3}
[*d1, *d2]

# ----------- OUTPUT --------- #
['key1', 'key2', 'key2', 'key3']
```

* But how can we unpack both key and value?
    

```python
d1 = {'key1': 1, 'key2': 2}
d2 = {'key2': 3, 'key3': 3}

{**d1, **d2}

# ------------ OUTPUT ---------- #
{'key1': 1, 'key2': 3, 'key3': 3}
```

* Notice that the value for key `key2` is 3 and not 2, but why?
    
* It's because the dictionary `d2` is merged last, so it overwrote the value for key `key2`.
    

#### Usage with Unordered Types

You can use the \* operator in unordered types, but the problem is you will never know what's the first element, what's the second element and so on.

* But this is useful when you want to unpack in the RHS.
    
* Let's say we have 3 dictionaries:
    
    * `d1 = {'p': 1, 'y': 2}`
        
    * `d2 = {'t': 3, 'h': 4}`
        
    * `d3 = {'h': 5, 'o': 6, 'n': 7}`
        
* Let's say we want to get all the unique keys, then what we can do is we can unpack all the keys of these dictionaries into a set.
    
* So, `s = {*d1, *d2, *d2}`.
    
* This will result in `s = {'p', 'y', 't', 'h', 'o', 'n'}`.
    

### Use case for \*\*

* You can't use the \*\* operator on the LHS, you can only use it on RHS.
    
* Let's say we have 3 dictionaries:
    
    * `d1 = {'p': 1, 'y': 2}`
        
    * `d2 = {'t': 3, 'h': 4}`
        
    * `d3 = {'h': 5, 'o': 6, 'n': 7}`
        
* `d = {**d1, **d2, **d3}`
    
* `d = {'p': 1, 'y': 2, 't': 3, 'h': 5, 'o': 6, 'n': 7}`
    
* As you may have noticed, the value of `h` in `d` is 5 even though there are two different values for the key `h`.
    
* The resulting dictionary took the value `5` because `d3` is mergerd at the end and it overwrote the value for the key `h`.
    
* You can even use it to add key-value pairs from one or more dictionaries into a dictionary literal.
    
* Let's say we have a dictionary `d1 = {'a': 1, 'b': 2}`.
    
* Let's say we create another dictionary and we want to add/merge the `d1` dictionary into this dictionary, then to do this:
    
* `d2 = {'a': 10, 'c': 3, **d1}`.
    
* This will result in `d2 = {'a': 1, 'b': 2, 'c': 3}`.
    
* You may ask why the value of `a` is 1.
    
* The reason is `d1` is merged at the end so it overwrote the value of `a`.
    

```python
d1 = {'key1': 1, 'key2': 2}
d2 = {'key2': 3, 'key3': 3}

{**d1, **d2}

# --------- OUTPUT ---------- #
{'key1': 1, 'key2': 3, 'key3': 3}
```

```python
{**d2, **d1}

# --------- OUTPUT ----------- #
{'key2': 2, 'key3': 3, 'key1': 1}
```

Here, you can see that the value for `key2` is 2 as `d1` is merged at the end.

```python
{'a': 1, 'b': 2, **d1, **d2, 'c':3}

# ---------- OUTPUT ----------- #
{'a': 1, 'b': 2, 'key1': 1, 'key2': 3, 'key3': 3, 'c': 3}
```

```python
{'key1': 100, **d1, **d2, 'key3': 200}
# ---------- OUTPUT ----------- #
{'key1': 1, 'key2': 3, 'key3': 200}
```

### Nested Unpacking

* Python supports nested unpacking as well.
    
* Let's say we have a nested list `l = [1, 2, [3, 4]]`.
    
* We can unpack this in multiple ways:
    
    * `a, b, c = l`, this will result in `a = 1`, `b = 2`, and `c = [3, 4]` and then we'll have to unpack `c`.
        
    * `a, b, (c, d) = l`, this will reslult in `a = 1`, `b = 2`, `c = 3`, `d = 4`.
        
    * The above method will work with string as well.
        
    * `a, *b, (c, *d) = [1, 2, 3, 'python']`
        
    * This will result in `a = 1`, `b = [2, 3]`, `c = 'p'`, and `d = ['y ,'t' ,'h' ,'o' ,'n']`.
        

```python
a, b, (c, d) = [1, 2, ['X', 'Y']]
print(a)
print(b)
print(c)
print(d)

# ---------- OUTPUT --------- #
1
2
X
Y
```

```python
a, b, (c, d) = [1, 2, 'XY']
print(a)
print(b)
print(c)
print(d)

# ----------- OUTPUT ----------- #
1
2
X
Y
```

```python
a, b, (c, d, *e) = [1, 2, 'python']
print(a)
print(b)
print(c)
print(d)
print(e)

# ---------- OUTPUT ---------- #
1
2
p
y
['t', 'h', 'o', 'n']
```

```python
a, *b, (c, d, *e) = [1, 2, 3, 'python']
print(a)
print(b)
print(c)
print(d)
print(e)

# ----------- OUTPUT ---------- #
1
[2, 3]
p
y
['t', 'h', 'o', 'n']
```

```python
a, *b, tmp = [1, 2, 3, 'python']
print(a)
print(b)
print(tmp)


# --------- OUTPUT --------- #
1
[2, 3]
python
```

```python
c, d, *e = tmp
print(c)
print(d)
print(e)

# ---------- OUTPUT ---------- #
p
y
['t', 'h', 'o', 'n']
```

## Args

* In Python, the `*args` concept is used to pass a variable number of arguments to a function. The `*args` parameter allows you to pass any number of positional arguments to a function, and it collects them into a tuple within the function. The asterisk (\*) before `args` is what enables this behavior.
    
* Now let's see how we can use \*args in function parameters.
    
* Recall that in unpacking, `a, b, *c = 10, 20, 'a', 'b'` will result in `a = 10`, `b = 20` and `c = ['a', 'b']`.
    

```python
a, b, *c = 10, 20, 'a', 'b'

print(a, b)
print(c)

# ------------ OUTPUT ------------ #
10 20
['a', 'b']
```

* A similar thing happens with function parameters.
    

```python
def func1(a, b, *args):
    print(a)
    print(b)
    print(args)

func1(1, 2, 'a', 'b')

# ------------ OUTPUT ------------ #
1
2
('a', 'b')
```

* In functions, args will be a tuple and not a list
    
* The `*args` syntax allows flexibility since you don't have to specify the exact number of arguments in advance. You can pass any number of arguments to the function, including none at all.
    
* The name of parameter args is a convention, you can use any name you want.
    

```python
def func1(a, b, *my_vars):
    print(a)
    print(b)
    print(my_vars)

func1(10, 20, 'a', 'b', 'c')

# ---------- OUTPUT ----------- #
10
20
('a', 'b', 'c')
```

* You can't use any positional arguments after the args parameter.
    
* When you call a function with some arguments, the arguments get unpacked in multiple variables which are the parameters of the function.
    

```python
# unpacking an iterable into positional arguments
def func1(a, b, c):
    print(a)
    print(b)
    print(c)

l = [10, 20, 30]
func1(*l)

# ------------ OUTPUT ------------ #
10
20
30
```

* Conventionally, we call it \*args.
    

## Args with keyword Arguments

* Let's recall positional arguments.
    

```python
def func1(a, b, c):
    print(a, b, c)

func1(10, 20, 30)

# --------------- OUTPUT ----------- #
10 20 30
```

* Here, `a = 10`, `b = 20` and `c = 30`.
    
* Remember, positional parameters defined in the function can also be passed as named/keyword arguments.
    

```python
func1(b=20, c=30, a=10)

# --------- OUTPUT --------- #
10 20 30
```

* We can make users use keyword arguments by exhausting all positional arguments using `*args`.
    

```python
def func1(a, b, *args, d):
    print(a, b, args, d)
    

func1(10, 20, 'a', 'b', d=100)

# ------------ OUTPUT ------------ #
10 20 ('a', 'b') 100
```

* Here, you can see the variables `a` and `b` gets assigned to the first and second arguments respectively, the args get assigned to the next two string arguments and finally the keyword argument `d` gets assigned to the value `100`.
    
* You can also use args when you don't want mandatory positional arguments.
    

```python
# optional positional arguments and mandatory keyword arguments
def func1(*args, d):
    print(args)
    print(d)

func1(1, 2, 3, d='hello')


# ---------- OUTPUT --------- #
(1, 2, 3)
hello
```

```python
func1(d='hello')

# ----------- OUTPUT ----------- #
()
hello
```

* Let's say you want a function that will only accept keyword arguments and no positional arguments.
    

```python
def func1(*, d='hello'):
    print(d)

func1(d='bye')


# ----------- OUTPUT ----------- #
bye
```

* In this function definition, the \* operator is used before the parameter list, indicating that all subsequent parameters should be keyword-only arguments. In other words, these parameters can only be passed using their corresponding keywords.
    
* Let's take another example, which takes no positional arguments and 2 keyword arguments.
    

```python
# two keyword arguments are compulsory
def func1(*, a, b):
    print(a)
    print(b)

func1(a=10, b=20)

# ------------ OUTPUT ---------- #
10
20
```

* Unlike positional parameters, keyword arguments do not have to be defined with non-defaulted and then defaulted arguments
    

```python
def func1(a, *, b='hello', c):
    print(a, b, c)

func1(5, c='bye')

# ---------- OUTPUT ---------- #
5 hello bye
```

* Here, `a = 5`, then `*` denotes no positional argument after this only keyword arguments will be allowed, then `c = 'bye'`, `b = 'hello'`.
    
* Let's see some examples.
    

```python
def func1(a, b=20, *args, d=0, e='n/a'):
    print(a, b, args, d, e)

func1(5, 4, 3, 2, 1, d=0, e='all engines running')

# ------------ OUTPUT ------------ #
5 4 (3, 2, 1) 0 all engines running
```

* Here, `a = 5`, `b = 4`, `args = (3, 2, 1)`.
    
* After this only keyword arguments are there and there are 2 keyword arguments.
    
* `d = 0` and `e = 'all engines running'`.
    

```python
func1(0, 600, d='goooood morning', e='python!')

# ----------- OUTPUT ----------- #
0 600 () goooood morning python!
```

* Here, `a = 0`, `b = 600`, and as there are no more positional arguments so `args = ()`.
    
* `d = goooood morning` and `e = 'python!'`.
    

```python
func1(11, 'm/s', 24, 'mph', d='unladen', e='swallow')

# ------------- OUTPUT ------------ #
11 m/s (24, 'mph') unladen swallow
```

* Here, `a = 11`, `b = 'm/s'`, `args = (24, 'mph')`.
    
* `d = 'unladen'` and `e = 'swallow'`
    

## kwargs

* \*args is used to scoop up a variable amount of remaining positional arguments and it returns a tuple.
    
* Here the parameter name args is arbitrary, the real parameter here is \*.
    
* \*\*kwargs is used to scoop up a variable amount of remaining keyword arguments.
    
* It'll return a dictionary
    
* \*\*kwargs can be specified even if the positional arguments have not been exhausted.
    
* Let's see some examples
    

```python
def func(**kwargs):
    print(kwargs)

func(x=100, y=200)

# ------------ OUTPUT ----------- #
{'x': 100, 'y': 200}
```

* We can also use it in conjunction with **\*args**:
    

```python
def func(*args, **kwargs):
    print(args)
    print(kwargs)

func(1, 2, a=100, b=200)

# ------------ OUTPUT ----------- #
(1, 2)
{'a': 100, 'b': 200}
```

* Note: You cannot do the following:
    

```python
def func(*, **kwargs):
    print(kwargs)
```

* There is no need to even do this, since **\*\*kwargs** essentially indicates no more positional arguments.
    

```python
def func(a, b, **kwargs):
    print(a)
    print(b)
    print(kwargs)

func(1, 2, x=100, y=200)

# ------------ OUTPUT ---------- #
1
2
{'x': 100, 'y': 200}
```

* Also, you cannot specify parameters **after** **\*\*kwargs** has been used:
    

```python
def func(a, b, **kwargs, c):
    pass

# ------------ OUTPUT ----------- #
	def func(a, b, **kwargs, c):
                             ^
SyntaxError: invalid syntax
```

* If you want to specify both specific keyword-only arguments and **\*\*kwargs** you will need to first get to a point where you can define a keyword-only argument (i.e. exhaust the positional arguments, using either **\*args** or just **\***)
    

```python
def func(*, d, **kwargs):
    print(d)
    print(kwargs)

func(d=1, x=100, y=200)

# ---------- OUTPUT ---------- #
1
{'x': 100, 'y': 200}
```

## Putting It All Together

```python
#positionals only
def func(a, b):
    print(a, b)

func('hello', 'world')

# ----------- OUTPUT --------- #
hello world
```

```python
func(b='world', a='hello')

# ------------ OUTPUT ------------ #
hello world
```

```python
#positionals only: no extra positionals, only defaults
def func(a, b='world', c=10):
    print(a, b, c)

func('hello')

# ----------- OUTPUT ------------ #
hello world 10
```

```python
func('hello', c='!')

# ----------- OUTPUT ----------- #
hello world !
```

```python
# positionals only: extra positionals, no defaults
def func(a, b, *args):
    print(a, b, args)

func(1, 2, 'x', 'y', 'z')

# ---------- OUTPUT ---------- #
1 2 ('x', 'y', 'z')
```

```python
# keywords only: no positionals, no defaults
def func(*, a, b):
    print(a, b)

func(a=1, b=2)

# ------------ OUTPUT ----------- #
1 2
```

```python
# keywords only: no positionals, some defaults
def func(*, a=1, b):
    print(a, b)

func(a=10, b=20)

# ---------- OUTPUT ----------- #
10 20
```

```python
func(b=2)

# ---------- OUTPUT ----------- #
1 2
```

```python
# keywords and positionals: some positionals(no defaults), keywords(no defaults)
def func(a, b, *, c, d):
    print(a, b, c, d)

func(1, 2, c=3, d=4)

# ----------- OUTPUT ---------- #
1 2 3 4
```

```python
func(1, 2, d=4, c=3)


# ---------- OUTPUT ---------- #
1 2 3 4
```

```python
func(1, c=3, d=4, b=2)

# ---------- OUTPUT ---------- #
1 2 3 4
```

```python
# keywords and positionals: some positional defaults
def func(a, b=2, *, c, d=4):
    print(a, b, c, d)

func(1, c=3)

# ------------ OUTPUT ----------- #
1 2 3 4
```

```python
func(c=3, a=1)

# ---------- OUTPUT ------------ #
1 2 3 4
```

```python
func(1, 2, c=3, d=4)

# ---------- OUTPUT ----------- #
1 2 3 4
```

```python
func(c=3, a=1, b=2, d=4)

# ---------- OUTPUT ---------- #
1 2 3 4
```

```python
# keywords and positionals: extra positionals
def func(a, b=2, *args, c=3, d):
    print(a, b, args, c, d)

func(1, 2, 'x', 'y', 'z', c=3, d=4)

# ----------- OUTPUT ----------- #
1 2 ('x', 'y', 'z') 3 4
```

```python
func(1, 'x', 'y', 'z', c=3, d=4)

# --------- OUTPUT ---------- #
1 x ('y', 'z') 3 4
```

```python
# keywrods and positionals: no extra positionals, extra keywords
def func(a, b, *, c, d=4, **kwargs):
    print(a, b, c, d, kwargs)

func(1, 2, c=3, x=100, y=200, z=300)

# ---------- OUTPUT ----------- #
1 2 3 4 {'x': 100, 'y': 200, 'z': 300}
```

```python
func(x=100, y=200, z=300, c=3, b=2, a=1)


# ----------- OUTPUT ------------ #
1 2 3 4 {'x': 100, 'y': 200, 'z': 300}
```

```python
# keywords and positionals: extra positionals, extra keywords
def func(a, b, *args, c, d=4, **kwargs):
    print(a, b, args, c, d, kwargs)

func(1, 2, 'x', 'y', 'z', c=3, d=5, x=100, y=200, z=300)

# ------------ OUTPUT ---------- #
1 2 ('x', 'y', 'z') 3 5 {'x': 100, 'y': 200, 'z': 300}
```

```python
#keywords and positionals: extra positionals and extra keywords
def func(*args, **kwargs):
    print(args, kwargs)

func(1, 2, 3, x=100, y=200, z=300)

# ----------- OUTPUT ------------- #
(1, 2, 3) {'x': 100, 'y': 200, 'z': 300}
```

# Conclusion

In conclusion, mastering Python function arguments is essential for writing efficient and clean code. By understanding the differences between parameters and arguments, utilizing positional and keyword arguments, and leveraging unpacking, *args, and* \*kwargs, you'll be better equipped to tackle complex programming tasks in Python.