# EX 4A DYNAMIC PROGRAMMING - 1
## DATE:
## AIM:
To find longest common subsequence using Dynamic Programming.



## Algorithm
1. Initialize a memoization table:
Create a 2D list c of size (len(u)+1) x (len(v)+1) to store LCS lengths of all substrings u[i:] and v[j:].

2. Set base cases:
Set the last row and last column of c to 0, representing LCS with an empty string.

3. Fill the table bottom-up:
For every index i from end to start of u, and j from end to start of v:

If u[i] == v[j]: set c[i][j] = 1 + c[i+1][j+1]

Else: set c[i][j] = max(c[i+1][j], c[i][j+1])

4. Reconstruct the LCS:
Starting from c[0][0], trace the path using the values:

If characters match, include it in the result and move diagonally

Else, move in the direction of the larger value (right or down)

5. Print the LCS:
As characters are matched during reconstruction, print them directly to output the LCS.   

## Program:
```
/*
Program to implement the longest common subsequence using Dynamic Programming.
Developed by: NAGINENI ROHITH
Register Number:  212222040105
*/
```
```
def lcs(u, v):
    """Return c where c[i][j] contains length of LCS of u[i:] and v[j:]."""
    c = [[-1]*(len(v) + 1) for _ in range(len(u) + 1)]
 
    for i in range(len(u) + 1):
        c[i][len(v)] = 0
    for j in range(len(v)):
        c[len(u)][j] = 0
 
    for i in range(len(u) - 1, -1, -1):
        for j in range(len(v) - 1, -1, -1):
            if u[i] == v[j]:
                c[i][j] = 1 + c[i + 1][j + 1]
            else:
                c[i][j] = max(c[i + 1][j], c[i][j + 1])
 
    return c
 
 
def print_lcs(u, v, c):
    """Print one LCS of u and v using table c."""
    i = j = 0
    while not (i == len(u) or j == len(v)):
        if u[i] == v[j]:
            print(u[i], end='')
            i += 1
            j += 1
        elif c[i][j + 1] > c[i + 1][j]:
            j += 1
        else:
            i += 1
 
 
u = input()
v = input()
c = lcs(u, v)

print_lcs(u, v, c)
```
## Output:

![image](https://github.com/user-attachments/assets/5bdd2e77-de71-4228-ac26-355b8a61fcfd)
## Result:
Thus the program was executed successfully for computing the length of longest common subsequence.
