# Problem
Write a function:

def solution(A)

that, given an array A of N integers, returns the smallest positive integer (greater than 0) that does not occur in A.

For example, given A = [1, 3, 6, 4, 1, 2], the function should return 5.

Given A = [1, 2, 3], the function should return 4.

Given A = [−1, −3], the function should return 1.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [−1,000,000..1,000,000].

# Solution
```
def solution(A):
    # Implement your solution here
    if all(ele != 1 for ele in A):
        return 1
    else:
        A_sorted = sorted(A) 
        j=0
        for j in range(len(A_sorted)-1):
            if A_sorted[j] > 0:
                if A_sorted[j+1] - A_sorted[j] > 1:
                    return A_sorted[j] + 1
            else:
                continue
        # no gap found
        if len(A_sorted) > 1:
            return A_sorted[j+1]+ 1
        else:
            return A_sorted[j] + 1
```

Passed 100%

Time Complexity O(N or O (N log(N))
