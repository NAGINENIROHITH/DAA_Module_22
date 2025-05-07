# EX 4B DYNAMIC PROGRAMMING – 2
## DATE:
## AIM:
To find the longest string (or strings) that is a substring (or are substrings) of two strings..



## Algorithm
1. Initialize a lookup table:
   Create a 2D table lookup[m+1][n+1] initialized with zeros, where m and n are lengths of strings X and Y.

2. Track length and position:
   Use variables maxLength to store the length of the longest common substring found so far and endingIndex to store its ending index in string X.

3. Fill the table:
  For each character pair (X[i-1], Y[j-1]), if they match:

  Set lookup[i][j] = lookup[i-1][j-1] + 1

  Update maxLength and endingIndex if a longer match is found.

4. Ignore mismatches:
   If characters don’t match, leave lookup[i][j] = 0 (i.e., reset substring length at that position).

5. Extract result:
   Use endingIndex and maxLength to slice and return the longest common substring from string X.   

## Program:
```
/*
Program to implement the longest common substring problem.
Developed by: NAGINENI ROHITH
Register Number: 212222040105 
*/
```
```
def LCS(X, Y, m, n):
 
    maxLength = 0           
    endingIndex = m         
    lookup = [[0 for x in range(n + 1)] for y in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if X[i - 1] == Y[j - 1]:
                lookup[i][j] = lookup[i - 1][j - 1] + 1
                if lookup[i][j] > maxLength:
                    maxLength = lookup[i][j]
                    endingIndex = i
    return X[endingIndex - maxLength: endingIndex]
 
 
if __name__ == '__main__':
 
    X = input()
    Y = input()
 
    m = len(X)
    n = len(Y)
    print('The longest common substring is', LCS(X, Y, m, n))
```
## Output:

![image](https://github.com/user-attachments/assets/6c725bdf-aaf7-43ed-9bae-f3259bc790ed)


## Result:
Thus the program was executed successfully for finding the longest common substring .
