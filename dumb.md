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


### POWER BI
- counting rows : count('tableName')
- creating a new Table : NumberTable = GENERATESERIES(1, 100, 1)
- Date table :
DateTable =
ADDCOLUMNS(
    CALENDAR (DATE(2020, 1, 1), DATE(2030, 12, 31)),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMMM"),
    "Quarter", "Q" & FORMAT([Date], "Q"),
    "Week Number", WEEKNUM([Date]),
    "Day", DAY([Date])

)
- running total : rng tot = caluculate(totalsum,filter(table[col1] <= table[col1]) )

---
✅ Java Class Hierarchy

LinkedList → implements → List, Queue, Deque

So you get all deque methods:

- addFirst()
- addLast()
- pollFirst()
- pollLast()
- peekFirst()
- peekLast()
- removeFirst()
- removeLast()
- for size() it uses internal counter and returns size is O(1)
---
