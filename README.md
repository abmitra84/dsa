# Problem
A non-empty array A consisting of N integers is given.

A permutation is a sequence containing each element from 1 to N once, and only once.

For example, array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
is a permutation, but array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
is not a permutation, because value 2 is missing.

The goal is to check whether array A is a permutation.

Write a function:

def solution(A)

that, given an array A, returns 1 if array A is a permutation and 0 if it is not.

For example, given array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
    A[3] = 2
the function should return 1.

Given array A such that:

    A[0] = 4
    A[1] = 1
    A[2] = 3
the function should return 0.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [1..1,000,000,000].

# Solution
```
def solution(A):
    # Implement your solution here
    A_sorted = sorted(A) 
    diffs = [1 if (A_sorted[i+1]-A_sorted[i]) != 1 else 0 for i in range(len(A_sorted)-1)]
    
    N = len(A_sorted)
    ideal_sum = N * (N+1)/2
    actual_sum = sum(A) 

    i = -1
    try:
        i = diffs.index(1)
        if i != -1:
            return 0
    except:
        if ideal_sum != actual_sum:
            return 0
        elif ideal_sum == actual_sum:
            if len(A) != max(A):
                return 0
            else:
                return 1
```
Time Complexity: O(N) or O(N log(N))
