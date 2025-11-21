### creating a 2d array in python
``` python
import numpy as np
arr = np.zeros((m,n)) # MxN
arr = [[0 for _ in range(n)] for _ in range(m)]
arr = [[0]*n]*m
```


### sql
- 22-11-2025 : timediff() can give wrong answers , use timestampdiff(second,min,max)   but in timediff(max,min)
- using ws_concat(null,colm1,colm2) is better than normal concat
