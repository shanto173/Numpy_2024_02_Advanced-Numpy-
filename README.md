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
