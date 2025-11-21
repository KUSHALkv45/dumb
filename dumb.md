### creating a 2d array in python
``` python
import numpy as np
arr = np.zeros((m,n)) # MxN
arr = [[0 for _ in range(n)] for _ in range(m)]
arr = [[0]*n]*m
```
