# Algorithms

## set of instructions to accomplish a task - every piece of code is an algorishm

# Day 1

[Guessing Game](https://www.khanacademy.org/computing/computer-science/algorithms/intro-to-algorithms/a/a-guessing-game)

### if we increase input size, how many more steps does this fnction need to take?

- increase input size --> compare to the function steps

-Constant Time `O(1)`
```python
def add(x, y):
    x + y
add(1, 2)
```
-Linear Time `O(n)`

```python
a_list = [1, 2, 3, 4, 5]

def print_list(arr):
    for thing in arr:
        print(thing)

print_list(a_list) # 5 loops

long_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print_list(long_list) # 10 loops

# double input size
# doubled the steps
# 1 to 1 ratio
# linear
# o(n)


def bar(x):

    sum = 0
    for i in range(0, 1463):
        i += 1
        for j in range(0, x):
            for k in range(x, x + 15):
                sum += 1

# 1463 * (1 + (n *(15 * 1)))
# 1463 * (1 + 15n)
# 1463  ...
# There is only one variable for fuct --> 
# O(n)
```

-Quadradic Time `O(n)^2`

```python
def nested_loop(arr):
    for thing in arr:
        for other_thing in arr:
            print(thing, other_thing)

nested_loop(a_list) # 25 loops

nested_loop(long_list) # 100 steps

nested_loop(list_100_steps_long) # 10000

# doubled input size
# quadrupled the steps!
# 1 to 4 ratio
# quadradic time complexity



# Cout all the steps
# then calculate Big O
```

- Logarithmic time `O(log(n))`

```python
def foo(n):
    sq_root = int(math.sqrt(n))
    for i in range(0, sq_root):
        print(i)

# O(log(n))
# 36 --> 6
# 100 --> 10
# 10000 --> 100
# As input increases or prosses slows

def bisect(n):
    while n > 1:
        n = n/2

#100 --> 50 --> 12.5 --> 6.25 --> 3 --> 1.5 --> 7.5~ 
#(2**7)
#Log is finding the number of steps - `7`
#log = (2 ** ?)
```

### Calc Time Complexity:

```python
def a_func(arr):
    a = 1
    b = 2
    c = 3

    for x in range(1000):
        print(x)

    for thing in arr:
        print(thing)

a_func(a_list)

# a_list
# 3 + 1000 + len(arr) `5`
# long list
# 3 + 1000 + `10`
# 

# Cout all the steps
# then calculate Big O


def a_func(arr):
    a = 1
    b = 2
    c = 3

    for x in range(1000):
        print(x)

    for thing in arr:
        x = 10
        y = 20
        z = x * y
        print(thing) # `4` steps

a_func(a_list)

# a_list
# 3 + 1000 + (`4` * len(arr) `5`)
# if `len(arr) == 4 trillion
# `4` becomes insignificant


```

### We say `"On the order of"` because we are only looking for the worst thing in the function

```python
def a_func(arr):
    a = 1
    b = 2
    c = 3

    for x in range(1000):
        print(x)

    for thing in arr:
        x = 10
        y = 20
        z = x * y
        print(thing) # `4` steps

a_func(a_list)

# a_list
# 3 + 1000 + (`4` * len(arr) `5`)
# if `len(arr) == 4 trillion
# `4` becomes insignificant
```

### 2 Loops

```python
def two_loops(arr):

    for x in range(100000000000):
        z = x * x
        print(z)

    for thing in arr:
        print(thing) 

    for thing_again in arr:
        print(thing_again)

```

> Big O? - line by line
>> `(big_num * 2) + len(arr) + len(arr)`

>> `(big_num * 2) + (2 * len(arr))`

>> we dont care about the big num because it is constant

>> `O(n)`

### Recursive function
```python
def simple_rec(n):
    if n <= 1:
        return n
    simple_rec(n -1) 

simple_rec(5) # 10 steps
simple_rec(10) # 20
# input doubles == time doubles
# O(n)


def weird_rec(num):
    if n<= 1:
        retrun n
    simple_rec(n - 1) # n1
    simple_rec(n - 1) # n2
    simple_rec(n - 1) # n3
# exponentia: 3^n
```

## Recursion:

```python
def two_n_demo(3):
    if n == 0:
        retrun 1
    a = two_n_demo(2)
    b = two_n_demo(n - 1)
    return a + b

# function works from top to bottom and back up again
```

##Sorting

- earier to search though

```python
arr = [4, 0, 5, 2, 3, 1]


# O(n) - worst case we need to sort to end of arr
def find_num(arr, target):
    for x in arr:
        if x == target:
            return x
    return -1

find_num(arr, 1)
```

### Insertion Sort:

[visualize insertion sort](https://www.hackerearth.com/ja/practice/algorithms/sorting/insertion-sort/visualize/)

pseudocode:

```
arr = [4, 2, 6, 9,]

>start looping at the 2nd element

    >>pick up current element and hold it

        >>>while current element is less than its left sibling - swap
            
            >>>>copy left sibling to the right

            >>>>decrement index

        >>>finally, put our current element down
```

```python
arr = [99, 98, 4, 0, 2, 3, 1]


# insertion sort works in place
def insertionSort(arr):
    # start looping at the 2nd element
    for idx in range(1, len(arr)): # multi num of steps taken here * num of steps taken below
        # pick up current element and hold it
        currE = arr[idx]
        currIdx = idx
        # while current element is less than its left sibling - swap
        while currE < arr[currIdx - 1]:
            # copy left sibling to the right
            arr[currIdx] = arr[currIdx - 1]
            # decrement index
            currIdx -= 1
            # finally, put our current element down
        arr[currIdx] = currE

# time complexity: n * (1 + 1 + (n * 2) + 1)
# n * (3 + 2n)
# 3n + 2n^2
# O(n + n^2)
# O(n^2)

# arr[i], arr[i - 1] = arr[i - 1], arr[i]
# ​insertionSort(arr)


print(insertionSort(arr))
```
[![sort dance](http://img.youtube.com/vi/ROalU379l3U/0.jpg)](https://www.youtube.com/watch?v=ROalU379l3U "sort dance")