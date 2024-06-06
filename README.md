# Problem
A string S consisting of N characters is considered to be properly nested if any of the following conditions is true:

S is empty;
S has the form "(U)" or "[U]" or "{U}" where U is a properly nested string;
S has the form "VW" where V and W are properly nested strings.
For example, the string "{[()()]}" is properly nested but "([)()]" is not.

Write a function:

def solution(S)

that, given a string S consisting of N characters, returns 1 if S is properly nested and 0 otherwise.

For example, given S = "{[()()]}", the function should return 1 and given S = "([)()]", the function should return 0, as explained above.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [0..200,000];
string S is made only of the following characters: '(', '{', '[', ']', '}' and/or ')'.
# Solution
```
def solution(S):
    # Implement your solution here
    stack = []
    pairs = ['()', '{}', '[]']

    if len(S) == 0:
        return 1
    else:
        for i in range(len(S)):
            stack.append(S[i])
            if len(stack) > 1:
                if (stack[-2]+stack[-1]) in pairs:
                    stack.pop()
                    stack.pop()
        if len(stack) == 0:
            return 1
        else:
            return 0
```

Time Complexity  O(n)

Passed 100%
