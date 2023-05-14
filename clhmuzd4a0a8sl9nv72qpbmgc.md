---
title: "Python Variables Explained: Memory, Mutability, and More"
seoTitle: "Python Variables Explained: Memory, Mutability and More"
seoDescription: "Master Python variables for efficient coding: memory management, mutability, reference counting, garbage collection, object mutability"
datePublished: Sun May 14 2023 03:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clhmuzd4a0a8sl9nv72qpbmgc
slug: python-variables-explained-memory-mutability-and-more
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683968472429/a12200b7-1732-45e0-9a66-cf2791aaf437.png
tags: programming-blogs, programming, python, python3, python-beginner

---

Welcome to my blog post where we will dive into the world of Python variables. If you are new to programming, don't worry, I have got you covered! In my [previous blog post](https://neuronize.dev/quick-python-primer-master-the-basics-in-20-minutes), I provided a refresher on the basics of Python programming language. Now, we will move on to the next level and take a closer look at variables in Python. Variables are one of the fundamental concepts in programming and mastering them is essential for writing efficient and effective code. So, let's get started and explore Python variables in-depth!

Let's first take a look at memory.

## Memory

You can think of memory as a set of blocks where each block has a unique address. Think of it like a real-world example where each house on a street has a unique address. In the same way, each block has a unique address.

![figure of memory with each block having it's own unique address](https://cdn.hashnode.com/res/hashnode/image/upload/v1683960631074/4cf799c1-2097-4b60-b4b6-fb19603a5d1d.png align="center")

Now, let's dive into variables.

## Variable

**What happens when you write** `a = 5`?

* Python creates an object in memory in some address, let's say `0x1000`.
    
* In this object, the value 5 is stored.
    

![vale 5 is stored in a object at address 0x1000](https://cdn.hashnode.com/res/hashnode/image/upload/v1683960718378/f8d867c1-ddf1-4d3f-adcc-a8c072d46752.png align="center")

* Here, a is you can think of an alias for the memory address `0x1000`.
    
* Here, `a` doesn't represent the value `5` instead it refers to the memory address `0x1000` and the address `0x1000` refers to the data stored in the object and the data is `5`.
    

![a is referencing to address 0x1000](https://cdn.hashnode.com/res/hashnode/image/upload/v1683960782879/f4c6d7e2-59f0-436a-8aca-ce6486ce3f93.png align="center")

* To find out the memory address of the object that the variable is referencing, you can use the `id()` function.
    

```python
# declared a variable a and stored a value 10
a = 10

# printing the value, it's decimal memory address and it's hex memory address
print(a)
print(id(a))
print(hex(id(a)))


# ---------------------- OUTPUT ------------------ #
10
4376986128
0x104e38210
```

Here, I declared a variable `a` with a value of 10. Let's understand what happened under the hood.

* First, python created an object at some memory address, let's say `0x1000`.
    
* In that object, python puts the value 10.
    
* Finally, variable `a` refers to the memory address `0x1000` that holds the object with the value 10. In the above code, I have printed out the value, the decimal format of the address that the variable `a` is referring to and the hexadecimal format of the address.
    

Let's take a look at another example.

```python
s = "hello"
print(s)
print(id(s))
print(hex(id(s)))

# ------------------------- OUTPUT --------------------- #
hello
4702080944
0x118440fb0
```

* First, python created an object at some memory address with the value `'hello'`.
    
* Then, the variable `s` refers to the memory address that holds the object with the value `'hello'`. In the above code, I have printed out the value, the decimal format of the address that the variable `a` is referring to and the hexadecimal format of the address.
    

## Reference Counting

* So, we just learned how the variables are referencing a memory address where an object is stored.
    
* We can count how many variables are pointing to that same memory address.
    
* Let's say we declared a variable `a = 5` and let's say the memory address where the object gets created is `0x1000`.
    
* Then the reference count to that memory address is 1.
    

![reference count goes to 1](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963033848/b4719fc6-f957-42f5-9386-9cdcd383ed36.png align="center")

* Let's say we declared another variable `b = a`, where `b` is not getting assigned to a value `5` instead `b` is referencing the variable `a` which in turn references the memory location `0x1000`.
    
* Hence, two variables are pointing to the memory address `0x1000`.
    
* So, the reference count of the memory address `0x1000` is 2.
    

![reference count goes to 2](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963120701/79ca5535-4af7-4573-a541-3b4b699fc035.png align="center")

* Let's say b got removed either `b` is out-of-scope or maybe gets assigned to a different memory location, then the reference count goes to 1.
    

![b got out of scope and reference count goes to 1](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963613430/499bb03d-e59e-4c60-b2a6-74424710229b.png align="center")

* Let's say `a` also got removed in one of the above ways, then the reference count goes to 0.
    

![reference count goes to 0](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963653254/0c050724-c32c-4b99-88b0-d4b1b73d9c7a.png align="center")

* At this point, the Python memory manager recognizes this and throws away the object that was there in that memory location.
    
* Finally, the space is freed.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963699406/e519b156-6fe8-45a0-8f53-5ad35ed26ff7.png align="center")

* `sys` module has a `getrefcount()` function that can be used to get the reference count.
    
* This takes one parameter the variables, but the downside is that it also adds one reference count to that object.
    
* There's also another way using `ctypes` module.
    

### getrefcount()

```python
import sys

# delcared a list with respective values, print it's id and then get the reference count
lst_1 = [1,2,3]
print(id(lst_1))
sys.getrefcount(lst_1)

# --------------------- OUTPUT --------------------- #
4389242752
2
```

* It says 2 as the method `getrefcount()` is also referencing the address, so the reference count increases, to get the actual reference count, just subtract 1 from the answer.
    

### ctypes

```python
# with `ctypes`, you can get the actual reference count as it takes the actual memory address and not the reference.
import ctypes

def ref_count(address):
    return ctypes.c_long.from_address(address).value

# here you can see you get 1 as the reference count which is correct
print(id(lst_1))
ref_count(id(lst_1))

# -------------------- OUTPUT ------------------ #
4389242752
1
```

## Garbage Collection

* Previously, we learned that as soon as the reference count goes to 0, the Python memory manager destroys the object that's in the memory location and free's up the memory location.
    
* But this doesn't work always and one of the cases where this doesn't work is circular references.
    
* Let's think of a scenario where variable `a` is referencing the variable `b` and variable `b` is referencing the variable `c`.
    

![a is referencing to b and b is referencing to c](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963750338/e662de45-30e2-4efb-ba0d-5580a525aff1.png align="center")

* Now, let's say we delete the variable `a`.
    
    ![reference count of 0x1002 is 0](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963825263/3b146713-d8a7-4386-9f65-053c9cb2d6b8.png align="center")
    
* Now, the reference count of `b` is 0 but the reference count of `c` is 1.
    
* So, the second object will be destroyed, then the reference count of the third object will become 0 and it'll get destroyed too.
    
* Now, let's say the variable `c` is also referencing the variable `b`. i.e `c = b` and after that, we removed variable `a`.
    

![circular reference between b and c](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963905326/f44e0085-bd97-4f15-aa11-d5b79c1711e8.png align="center")

* Now, both object has reference count = 1.
    
* Now, none of the objects are going to get destroyed as both have a reference count of 1 and this scenario is known as circular referencing.
    
* As python memory manager can't eliminate these objects and if we continue like this, this will result in a memory leak.
    
* Here, the Garbage collector comes to the rescue, it can handle this kind of issue.
    
* You can control the garbage collector programmatically using `gc` module.
    
* You can call it manually and even do your cleanup.
    

```python
import gc
import ctypes

# function to count the references
def ref_count(address):
    return ctypes.c_long.from_address(address).value
```

* I imported the gc and ctypes modules and defined the reference count function to count the reference count.
    

```python
# this function will return if the given object_id is in the garbage collector or not
def object_by_id(object_id):
    for obj in gc.get_objects():
        if id(obj) == object_id:
            return "Object exists"
    return "Not found"
```

* This function will take the id of an object as an argument and then it'll return "Object exists" if the garbage collector has tracked that this object is in some circular reference else it'll return "Not found" i.e. the given object is not in any circular reference.
    

```python
# created two classes to illustrate the circular reference concept
class A:
    def __init__(self):
        self.b = B(self)
        print('A: self: {0}, b:{1}'.format(hex(id(self)), hex(id(self.b))))
        
        
class B:
    def __init__(self, a):
        self.a = a
        print('B: self: {0}, a: {1}'.format(hex(id(self)), hex(id(self.a))))
```

* Now, I created two classes A and B to illustrate the circular reference.
    
* `class A`: - This line defines a new class called A.
    
* `def __init__(self)`: - This is the constructor of the A class. It is executed when a new instance of the class is created.
    
* `self.b = B(self)` - This line creates a new instance of the B class and assigns it to the b attribute of the current instance of the A class. The self-argument passed to the B constructor is a reference to the current instance of the A class.
    
* `print('A: self: {0}, b:{1}'.format(hex(id(self)), hex(id(self.b))))` - This line prints a message to the console. The message contains the hexadecimal representations of the memory addresses of the current instance of the A class and its b attribute.
    
* `class B`: - This line defines a new class called B.
    
* `def __init__(self, a)`: - This is the constructor of the B class. It is executed when a new instance of the class is created. The `a` argument is a reference to an instance of the A class.
    
* `self.a` = a - This line assigns the `a` argument to the `a` attribute of the current instance of the B class.
    
* `print('B: self: {0}, a: {1}'.format(hex(id(self)), hex(id(self.a))))` - This line prints a message to the console. The message contains the hexadecimal representations of the memory addresses of the current instance of the B class and its `a` attribute.
    

```python
# We disabled the garbage collector, so that we can run it manually and also check the reference count.
gc.disable()
```

Now, we disabled the garbage collector, so that we can run it manually.

```python
# create an instance of class A
my_var = A()


# -------------- OUTPUT --------------- #
B: self: 0x11953e8c0, a: 0x11953d8d0
A: self: 0x11953d8d0, b:0x11953e8c0
```

* I created an instance of A.
    
* This prints out the ids of `a` and `b`.
    
* The id of `my_var` and `a` is the same.
    

```python
print('a: \t{0}'.format(hex(id(my_var))))
print('a.b: \t{0}'.format(hex(id(my_var.b))))
print('b.a: \t{0}'.format(hex(id(my_var.b.a))))

# ----------------- OUTPUT ------------------ #
a: 	0x119554e50
a.b: 	0x11953e680
b.a: 	0x119554e50
```

```python
# created two variables to store the ids of a and b instances
a_id = id(my_var)
b_id = id(my_var.b)
```

* These two variables are used to store the ids of `a` and `b`.
    

```python
# printing the refernce count of a and b
# printing if the object is in garbage collector or not
print('refcount(a) = {0}'.format(ref_count(a_id)))
print('refcount(b) = {0}'.format(ref_count(b_id)))
print('a: {0}'.format(object_by_id(a_id)))
print('b: {0}'.format(object_by_id(b_id)))

# --------------------- OUTPUT -------------------- #
refcount(a) = 2
refcount(b) = 1
a: Object exists
b: Object exists
```

* Here, I'm printing the reference count for `a` and `b`.
    
* I'm also checking if these objects are tracked by garbage collector or not.
    
* As you can see, the garbage collector tracked these two variables and returned "Object exists" for both of them as both of them are in a circular reference.
    

Now, let's point `my_var` to `None`, so we'll only have a circular reference.

```python
my_var= None
```

```python
print('refcount(a) = {0}'.format(ref_count(a_id)))
print('refcount(b) = {0}'.format(ref_count(b_id)))
print('a: {0}'.format(object_by_id(a_id)))
print('b: {0}'.format(object_by_id(b_id)))

# ------------------ OUTPUT -------------------- #
refcount(a) = 1
refcount(b) = 1
a: Object exists
b: Object exists
```

* Here, you can see that the reference count of `a` is decreased to 1 as we changed the `my_var` to refer to `None`.
    

```python
gc.collect()
print('refcount(a) = {0}'.format(ref_count(a_id)))
print('refcount(b) = {0}'.format(ref_count(b_id)))
print('a: {0}'.format(object_by_id(a_id)))
print('b: {0}'.format(object_by_id(b_id)))

# --------------- OUTPUT ----------------- #
refcount(a) = 0
refcount(b) = 0
a: Not found
b: Not found
```

We enabled the garbage collector and then the garbage collector removed both the objects and you can see that both the objects are not found.

## Object Mutability

* Changing the data inside the object is called modifying the internal state of the object.
    
* An object whose internal state can be changed is called mutable otherwise it's immutable.
    
* Immutable data types in Python are:
    
    * Numbers
        
    * Strings
        
    * Tuples
        
    * Frozen Sets
        
    * User Defined Classes
        
* Mutable data types in Python are:
    
    * Lists
        
    * Sets
        
    * DIctionaries
        
    * User-Defined Classes
        

Now, let's see some examples of mutable and immutable datatypes and understand what happens under the hood of mutable and immutable datatypes when you change their values.

### Immutable

* Let's say we have a string `s = 'python'`.
    
    ![s is referencing to 0x1000 where "python" is stored](https://cdn.hashnode.com/res/hashnode/image/upload/v1683963997841/89022a06-b180-4348-ba71-7aa8a34b25ae.png align="center")
    
* As we know, strings are immutable
    
* So, if in the next line, you'll write `s = 'hello'`.
    
* First, python will create another object at some different memory address with the value 'hello'.
    
    ![create new object and stored hello value](https://cdn.hashnode.com/res/hashnode/image/upload/v1683964046741/920b4819-5c49-4322-af23-973f10fc8907.png align="center")
    
* Then the variable `s` will point to this new object's address.
    
    ![s is not pointing to new object](https://cdn.hashnode.com/res/hashnode/image/upload/v1683964085540/20878b98-24cc-4914-903f-f8ecd8f701e7.png align="center")
    
* After this, the previous object with the value 'python' will be destroyed as no one is referencing that object.
    
* So, the python memory manager will destroy the object and free up the space.
    

![the old address is freed](https://cdn.hashnode.com/res/hashnode/image/upload/v1683964173422/6c7add81-667d-4bef-8165-fe0f539b634d.png align="center")

```python
s = 'python'
print(s)
print(hex(id(s)))

# ----------------- OUTPUT ------------------ #
python
0x10380b870
```

```python
s = 'hello'
print(s)
print(hex(id(s)))

# -------------- OUTPUT ------------------- #
hello
0x106232470
```

* As you can see both the addresses are different.
    

### Mutable

* Let's say we have a list `a = [1, 2, 3]`.
    
* As we know, lists are mutable i.e. elements can be inserted, deleted and replaced.
    
* When we write `a = [1, 2, 3]`, python creates an object at some memory location let's say `0x1000`.
    
    ![a is referencing to the address 0x1000](https://cdn.hashnode.com/res/hashnode/image/upload/v1683964208562/4b192a66-8ce5-42ea-a96a-99a8c1f7be4a.png align="center")
    
* Now, `a` points to the address `0x1000` where the list is stored.
    
* Let's say you wrote `a.append(4)`, to append 4 in the list `a`.
    
* Unlike Immutable datatypes, python won't create a new object instead it will add the value 4 to the object that is stored in `0x1000`.
    

![the list is modified and no new object is created](https://cdn.hashnode.com/res/hashnode/image/upload/v1683964280809/bc6bae8a-5c68-46e0-b757-c920d2b25ff5.png align="center")

```python
# creating a list and printing out the list and it's address
my_list = [1, 2, 3]
print(my_list)
print(hex(id(my_list)))

# ------------------- OUTPUT ------------------ #
[1, 2, 3]
0x11bf06340
```

```python
# checking if the address is changed after modifying the list

my_list.append(4)

print(my_list)

print(hex(id(my_list)))

# ------------------ OUTPUT -------------------- #
[1, 2, 3, 4]
0x11bf06340
```

* You can see that the address remains the same. Let's take another example
    

```python
# creating a dictionary and printing the dictionary and it's address
my_dict = {'key1': 1, 'key2': 2}
print(my_dict)
print(hex(id(my_dict)))

# ------------------ OUTPUT --------------- #
{'key1': 1, 'key2': 2}
0x11be9ea80
```

```python
# checking if the address is changed after modifying the dictionary
my_dict['key1'] = 10
print(my_dict)
print(hex(id(my_dict)))

# ---------------- OUTPUT ----------------- #
{'key1': 10, 'key2': 2}
0x11be9ea80
```

* As a dictionary is mutable, its address remains the same
    

### Mutable Datatype Within Immutable Datatype

* Let's take another tuple `b = ([1,2,3], [4,5,6])`
    
* As we know, lists are mutable i.e. elements can be inserted, deleted or replaced.
    
* Here, we can modify the lists that are in the tuple, but we can't make nay changes to the tuple i.e we can't insert a new element to the tuple, we can't delete an element from the tuple, we can't delete element from the tuple.
    
* Tuple still has the same elements, but as the elements are mutable we can make changes to those elements.
    

```python
a = [1, 2]
b = [3, 4]
t = (a, b)
print(hex(id(a)))
print(hex(id(b)))
print(hex(id(t)))

# ----------------- OUTPUT ---------------- #
0x10699f400
0x106f1dbc0
0x106f1d540
```

```python
a.append(3)
b.append(5)
print(t)
print(hex(id(a)))
print(hex(id(b)))
print(hex(id(t)))

# ---------------- OUTPUT ---------------- #
([1, 2, 3], [3, 4, 5])
0x10699f400
0x106f1dbc0
0x106f1d540
```

* Here, we only modified the lists and as they are mutable there addresses haven't changed.
    
* We haven't modified the tuple, the tuple always had those two lists, we didn't replace, deleted or inserted anything into this tuple, that's why its address also remains the same.
    

## Function Arguments and Mutability

* Let's see how the above concept of mutability and immutability affects function arguments.
    
* If the argument of the function is immutable, then it won't change.
    
* If the argument of the function is mutable, then it'll change.
    
* Let's take the help of an example and understand.
    

### Immutable Objects as Arguments

* Let's create a function `process(s)` that takes a string parameter.
    
* Remember, a string is an immutable object.
    

```python
# trying the similar thing with mutable and immutable objects but now the objects are passed as arguments to function
def process(s):
    print('initial s # = {0}'.format(hex(id(s))))
    s = s + ' world'
    print('s after change # = {0}'.format(hex(id(s))))
```

* First, I printed out the memory address where the string object is stored.
    
* Then, I concatenated another string `world` to string variable `s`.
    
* As you already know, modifying immutable objects is not possible.
    
* So, first, python created another string object with this new concatenated value `'hello world'`, then string variable `s` points to the new object where the `'hello world'` string is stored.
    
* In the end, you can see that the memory address where string variable `s` is pointing to is now different than the previous address.
    

```python
my_var = 'hello'
print('my_var # = {0}'.format(hex(id(my_var))))
```

* Here, I created a string called `my_var` which is referencing a memory address that has an object with the value `'hello'`.
    
* Printing the memory address where the string variable `my_var` is pointing.
    

```python
process(my_var)
```

* Then, I called the function `process(my_var)` and passed `my_var` as an argument.
    

```python
print('my_var # = {0}'.format(hex(id(my_var))))
```

* Now, you can see that the memory address of the string variable `my_var` is still the same because `my_var` is still pointing to the memory address where the string object with the value `'hello'` is stored.
    

### Mutable Objects as Arguments

* Let's create a function `process(items)` that takes a list parameter.
    
* Remember, a list is a mutable object.
    

```python
def modify_list(items):
    print('initial items # = {0}'.format(hex(id(items))))
    if len(items) > 0:
        items[0] = items[0] ** 2
    items.pop()
    items.append(5)
    print('final items # = {0}'.format(hex(id(items))))
```

* First, I printed out the memory address where the parameter `items` is pointing to.
    
* Then, I modified every element of that list, removed an element from that list and finally append 5 to that list.
    
* As you already know, modifying mutable objects is possible.
    
* So, first, python simply modified the object.
    
* In the end, you can see that the memory address where the list parameter `items` is pointing to, is same as the previous address.
    

```python
my_list = [2, 3, 4]
print('my_list # = {0}'.format(hex(id(my_list))))
```

* Here, I created a list `my_list` and print out the memory address where the `my_list` variable is pointing to.
    

```python
modify_list(my_list)
```

* Now, I called the function `modify_list(my_list)` with `my_list` variable as an argument.
    

```python
print(my_list)
print('my_list # = {0}'.format(hex(id(my_list))))
```

* Finally, I'm printing the variable `my_list`, to check whether `my_list` is modified or not.
    
* You can see that `my_list` is modified and this makes sense as the list is mutable.
    

### Mutable Objects inside Mutable Objects as Arguments

* Let's create a function `modify_tuple(t)` that takes a tuple parameter.
    
* Remember, a tuple is an immutable object while a list is a mutable object.
    

```python
def modify_tuple(t):
    print('initial t # = {0}'.format(hex(id(t))))
    t[0].append(100)
    print('final t # = {0}'.format(hex(id(t))))
```

* First, I printed out the memory address where the parameter `t` is pointing to.
    
* Then, I modified the first element of the tuple which is a list, here I appended the value 100.
    
* As you already know, modifying mutable objects is possible.
    
* So, first, python simply modified the list.
    
* In the end, you can see that the memory address where the tuple parameter `t` is pointing to, is the same as the previous address.
    

```python
a = [1,2,3]
b = [10,20,30]
my_tuple = (a,b)
```

* I created two lists `a` and `b` and then created a tuple `my_tuple` containing these two lists.
    

```python
hex(id(my_tuple))
```

* Here, I'm printing the memory address where the tuple `my_tuple` is pointing to.
    

```python
modify_tuple(my_tuple)
```

* Now, I called the function `modify_tuple(my_tuple)` with `my_tuple` as an argument, that will modify the list `a` in the tuple.
    

```python
my_tuple
```

* You can see that the tuple's content remains the same i.e. there are two lists `a` and `b` but the list `a` content/data is changed and it is possible as lists are mutable.
    

## Shared References and Mutability

* Shared reference is the concept of two variables referencing the same object or same memory address.
    
* Let's say we create two variables `a = 10` and `b = a`.
    
* Let's say that `a` is pointing to the memory address `` `0x1000` ``.
    
* So, `b` is also pointing to that same address.
    
* Hence, the reference count of that address is 2.
    

```python
# both the of the variables refer to the same address
my_var_1 = 'hello'
my_var_2 = my_var_1
print(my_var_1)
print(my_var_2)
```

* Here, I created two variables `my_var_1` and `my_var_2`.
    
* `my_var_1` is pointing to a memory address where an object with the value `'hello'` is stored.
    
* `my_var_2` is referencing `my_var_1` which in turn points to the memory address where the object with the value `'hello'` is stored.
    
* So, `my_var_2` is also referencing the same memory address as `my_var_1`.
    
* Finally, I'm printing the values of both variables.
    

```python
print(hex(id(my_var_1)))
print(hex(id(my_var_2)))
```

* Here, I'm printing the memory address that both of these variables are pointing to.
    

```python
# by modifying the address will change as string is immutable
my_var_2 = my_var_2 + ' world!'
```

* As I modified `my_var_2` , `my_var_2` will point to some other location where this new object is stored.
    

```python
print(hex(id(my_var_1)))
print(hex(id(my_var_2)))
```

* Now, you can see both the variables are pointing to different locations.
    

The same thing will happen with mutable objects.

```python
# doing the same thing with mutable objects
my_list_1 = [1, 2, 3]
my_list_2 = my_list_1
print(my_list_1)
print(my_list_2)
```

```python
print(hex(id(my_list_1)))
print(hex(id(my_list_2)))
```

* Similarly, as above both these lists are pointing to the same location.
    

```python
# it'll change both the lists as list is mutable.
my_list_2.append(4)
```

* Here, I'm modifying the list `my_list_2`.
    

```python
print(my_list_2)
print(my_list_1)
```

* You can see both the lists got modified as lists are mutable, so when I modified the object where the `my_list_2` is pointing to, python didn't create another object instead python modified the same object.
    
* Due to this, both the lists are showing the modified list.
    

```python
print(hex(id(my_list_1)))
print(hex(id(my_list_2)))
```

* You can see both lists are pointing to the same address even after modifying a list.
    

## Python Interning

* In Python, interning is a technique used to optimize the use of memory by storing the commonly used objects in a cache to avoid creating new objects each time they are needed.
    
* Two common types of objects that are interned in Python are integers and strings.
    

### Integer Interning

* Integer interning is the process of storing and reusing integer objects with values ranging from -5 to 256.
    
* When you create an integer object in this range, Python checks if it already exists in memory. If it does, it returns the reference to the existing object instead of creating a new one.
    
* This can improve the performance of Python programs by reducing the number of objects created and the amount of memory used. For example:
    

```python
a = 10
b = 10
a is b
True
```

In this example, both `a` and `b` are assigned the integer value `10`. Since this value is within the range of interned integers, Python interns it and assigns the same object to both `a` and `b`. Therefore, `a is b` returns `True`.

### String Interning

* String interning is the process of storing and reusing string objects with the same value.
    
* When you create a string object in Python, it is added to a cache of commonly used strings. If another string with the same value is created, Python returns a reference to the existing object instead of creating a new one.
    
* This can also improve the performance of Python programs by reducing the number of objects created and the amount of memory used. For example:
    

```python
a = 'hello'
b = 'hello'
a is b
True
```

* In this example, both `a` and `b` are assigned the string `'hello'`. Since this string is commonly used, Python interns it and assigns the same object to both `a` and `b`. Therefore, `a is b` returns `True`.
    

It is important to note that interning is an implementation detail of the Python language and may vary depending on the Python interpreter being used. Therefore, it is recommended to rely on the `==` operator to compare values of integers and strings instead of using the `is` operator.

## Variable Equality

* We can compare variables in two ways, one way is Memory address and the other one is data/content inside the object.
    
* To compare memory addresses of variables we can use `is` operator, which is known as an identity operator.
    

```python
print("a is b: ", a is b)
```

* To compare the data/content of the objects, we can use `==` operator, which is known as an equality operator.
    

```python
print("a == b:", a == b)
```

* If you want to check if two variables memory addresses are not equal, then you can use `is not` operator.
    
* If you want to check if two variable's data/content is not equal, then you can use `!=` operator.
    
* The `None` object can be assigned to variables to indicate that they are not set in the way we would expect them to be.
    
* For example, let's say we have a string s set to None, as we don't have any proper value, we just initialized the string with None.
    

```python
a = None
print(type(a))
print(hex(id(a)))
```

```python
a is None

True
```

```python
b = None
hex(id(b))

a is b
a == b
```

* None object is a real object, that is managed by the Python memory manager.
    

```python
hex(id(None))
type(None)
```

* Python memory manager will always use a shared reference when assigning a variable to None.
    

## Everything is an Object

* In Python, everything is an object. This means that any value, variable, or function in Python is considered an object.
    
* An object in Python is a self-contained piece of code that has data and methods that can be accessed and manipulated.
    
* Objects are instances of classes, which are essentially blueprints that define the structure and behavior of the objects.
    

For example, if you declare a variable in Python, such as:

```python
x = 42
```

The value `42` is an object of the `int` class, which means it has built-in methods and attributes that can be accessed and manipulated. Similarly, if you define a function in Python, such as:

```python
def my_function():
    print("Hello, World!")
```

The function `my_function()` is an object of the `function` class, which means it can be passed around as a variable, returned from another function, or even assigned to a different name.

The concept of everything being an object in Python is a fundamental aspect of the language and is important for understanding how Python code is executed and how objects interact with one another. It also allows for powerful programming constructs such as dynamic typing, duck typing, and metaprogramming, which can make Python code more flexible and expressive.

* Any object can be assigned to a variable, so functions(as a function is an object too) can also be assigned to a function.
    
* Any object can be passed to a function, therefore functions can be passed to a function.
    
* Any object can be returned from a function, therefore functions can be returned from a function.
    

## Conclusion

In conclusion, understanding variables and their behavior in Python is crucial for writing effective and efficient code. Variables are placeholders for data that are stored in memory, and their mutability determines whether they can be changed or not. Memory management is an important consideration when working with variables, as it can impact the performance of your code. Shared references can lead to unexpected results, so it is important to be aware of how they work. Finally, understanding function argument mutability can help you avoid errors when passing variables between functions. By keeping these concepts in mind, you can write better Python code and avoid common pitfalls.