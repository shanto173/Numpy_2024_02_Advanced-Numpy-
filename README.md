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




























