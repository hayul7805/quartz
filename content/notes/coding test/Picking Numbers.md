---
title: "Picking Numbers"
---

> Given an array of integers, find the longest subarray where the absolute difference between any two elements is less than or equal to 1. 

**Example**

a = [1,1,2,2,4,4,5,5,5]

There are two subarrays meeting the criterion:  [1,1,2,2,] and [4,4,5,5,5]. The maximum length subarray has 5 elements.

**Function Description**

Complete the _pickingNumbers_ function in the editor below. 

pickingNumbers has the following parameter(s): 

- int a[n] : an array of integers 

**Returns**

- int : the length of the longest subarray that meets the criterion 

**Input Format**

The first line contains a single integer _n_, the size of the array _a_.   
The second line contains _n_ space-separated integers, each *a[i]* .

**Constraints**
- 2 <= n <= 100
- 0 < a[i] < 100
-   The answer will be => 2. 

**Sample Input 0**

```
6
4 6 5 3 3 1
```

**Sample Output 0**

3

**Explanation 0**

We choose the following multiset of integers from the array: {4,3,3}. Each pair in the multiset has an absolute difference  <= 1(i.e., |4-1| = 1 and |3-3| = 0), so we print the number of chosen integers, 3, as our answer.

## 나의 풀이

```python
import math
import os
import random
import re
import sys
from collections import Counter

def pickingNumbers(a):
   
 # imput is un array of numbers.
    count_nums = Counter(a)
    max_num = 0
    
    for i in range(1, 100):

        max_num = max(max_num, 
				  count_nums[i] + count_nums[i+1])
    return max_num

if __name__ == '__main__':
    fptr = open(os.environ['OUTPUT_PATH'], 'w')
    
    n = int(input().strip())
    a = list(map(int, input().rstrip().split()))
    
    result = pickingNumbers(a)
    
    fptr.write(str(result) + '\n')
    fptr.close()
```

> [!note]  Note  
>   
> 이 문제는 `Counter()`로 일단 세고 시작하면 간단한다.
> 개수를 센 이후에는 양 옆의 크기를 더한 것이 가장 큰 경우가 답이므로.
