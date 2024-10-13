# NumPy Arrays vs Python Lists

This repository demonstrates the advantages of using NumPy arrays over Python lists in terms of speed, memory efficiency, convenience, and advanced indexing features.

## 1. Speed Comparison

### Python Lists:
```python
a = [i for i in range(10000000)]
b = [i for i in range(10000000,20000000)]

c = []
import time

start = time.time()
for i in range(len(a)):
    c.append(a[i] + b[i])
print(time.time()-start)  # Output: 3.2699835300445557 seconds
```

### NumPy Arrays:
```python
import numpy as np
a = np.arange(10000000)
b = np.arange(10000000,20000000)

start = time.time()
c = a + b
print(time.time()-start)  # Output: 0.06481003761291504 seconds
```

Result: NumPy arrays are significantly faster, performing over 54 times faster in this example.

### Why numpy faster?
- Numpy uses C programming type array (which means it is a static array,fixed-size array) which is why it is faster
- numpy array is not a referential array (meaning in memory numpy directly stores items/values, not the item address)

### Why Python list is slow?
#### There are 2 main reasons.
- it is a dynamic array, when the list gets full of items, it creates a new list whose size is double the previous list and has to copy all the value from the old list.because of this reason, it takes a lot of time
- python list are a referential array(meaning it is not direactly store item instead it used item address, then go to the memory to fetch all the item) 


## 2. Memory Comparison

### Python Lists:
```python
a = [i for i in range(10000000)]
import sys
sys.getsizeof(a)  # Output: 81528048 bytes
```

### numpy Arrays:

```python

a = np.arange(10000000, dtype=np.int8)
sys.getsizeof(a)  # Output: 10000104 bytes

```
Result: NumPy arrays use much less memory than Python lists.




## 3. Convenience

NumPy arrays provide more convenience than Python lists for tasks that involve complex numerical operations, matrix manipulations, and high-performance computations due to their optimized structure and built-in functions. Here’s why:

- **Element-wise operations**: In NumPy, you can directly perform operations on arrays element-wise without having to loop over individual elements like you would in Python lists.
- **Broadcasting**: NumPy allows operations between arrays of different shapes, automatically adjusting the shapes where necessary (broadcasting), which is not available with Python lists.
- **Advanced indexing**: NumPy allows sophisticated slicing and indexing techniques, making data manipulation easier.
- **Performance**: NumPy is implemented in C and optimized for performance, making it much faster for large data sets than Python lists.

### Example: Adding two lists in Python vs NumPy

#### Python List Example

This process requires manually looping through each element, adding complexity and decreasing performance for large datasets.

```python

# Python lists
a = [1, 2, 3, 4]
b = [5, 6, 7, 8]

# Adding two lists element-wise (manual loop)
c = []
for i in range(len(a)):
    c.append(a[i] + b[i])

print("Result using Python list:", c)

Result using Python list: [6, 8, 10, 12]
```

#### NumPy Array Example

In NumPy, the operation is much simpler and faster since you can directly add two arrays without looping.

```python

import numpy as np

# NumPy arrays
a = np.array([1, 2, 3, 4])
b = np.array([5, 6, 7, 8])

# Adding two arrays element-wise (direct operation)
c = a + b

print("Result using NumPy array:", c)
Result using NumPy array: [ 6  8 10 12]


```


## 4. Indexing

NumPy provides more efficient ways to work with arrays using advanced indexing techniques.

#### Normal Indexing and Slicing:

```python
a = np.arange(24).reshape(6, 4)
print(a[1, 2])  # Output: 5
print(a[1:3, 1:3])  # Output: array([[5, 6], [9, 10]])

```
### Fancy Indexing:

A fancy index gets used when we want to fetch rows and columns and can't be fetched through normal indexing because there are no pattern matches so we use fancy indexing.  

```python
print(a[:, [0, 2, 3]])
# Output:
# array([[ 0,  2,  3],
#        [ 4,  6,  7],
#        [ 8, 10, 11],
#        [12, 14, 15],
#        [16, 18, 19],
#        [20, 22, 23]])

```
#### Boolean Indexing:
```python

a = np.random.randint(1, 100, 24).reshape(6, 4)
print(a[a > 50])  # Output: All elements greater than 50

```





































































