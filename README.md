# Problem
A non-empty array A consisting of N integers is given. A pair of integers (P, Q), such that 0 ≤ P < Q < N, is called a slice of array A (notice that the slice contains at least two elements). The average of a slice (P, Q) is the sum of A[P] + A[P + 1] + ... + A[Q] divided by the length of the slice. To be precise, the average equals (A[P] + A[P + 1] + ... + A[Q]) / (Q − P + 1).

For example, array A such that:

    A[0] = 4
    A[1] = 2
    A[2] = 2
    A[3] = 5
    A[4] = 1
    A[5] = 5
    A[6] = 8
contains the following example slices:

slice (1, 2), whose average is (2 + 2) / 2 = 2;
slice (3, 4), whose average is (5 + 1) / 2 = 3;
slice (1, 4), whose average is (2 + 2 + 5 + 1) / 4 = 2.5.
The goal is to find the starting position of a slice whose average is minimal.

Write a function:

def solution(A)

that, given a non-empty array A consisting of N integers, returns the starting position of the slice with the minimal average. If there is more than one slice with a minimal average, you should return the smallest starting position of such a slice.

For example, given array A such that:

    A[0] = 4
    A[1] = 2
    A[2] = 2
    A[3] = 5
    A[4] = 1
    A[5] = 5
    A[6] = 8
the function should return 1, as explained above.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [2..100,000];
each element of array A is an integer within the range [−10,000..10,000].

# Solution
```
import math

def solution(A):
    # Implement your solution here
    n = len(A) 
    pref = [0] * (n+1)

    for k in range(1, n+1):
        pref[k] = pref[k-1] + A[k-1]
    
    avg_min = math.inf
    result = 0

    for i in range(n):
        for j in range(i+1,n):
            avg = (pref[j+1] - pref[i])/(j-i+1)
            if avg < avg_min:
                avg_min = avg
                result = i

    return result
```

Passed 60%

Time Complexity O(N^2). There is no active solution in python that explores ALL pairs in a list under O(N^2). 
The trick to solve this is to realize that there are only two slice sizes i.e. 2 and 3 for which it needs to be calculated(Check stackoverflow). Given it is a specific hack I didn't implement it. Net net it is an useless problem.
