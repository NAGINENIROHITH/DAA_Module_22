# EX 4C DYNAMIC PROGRAMMING – 3
## DATE:
## AIM:
Given a sequence, find the length of the longest palindromic subsequence in it.


## Algorithm
1. Reverse the input string:
   Copy the original string seq to another string s2, then reverse s2. The LPS problem becomes a Longest Common Subsequence (LCS) problem between seq and its 
   reverse.

2. Initialize DP table:
   Create a 2D memoization table dp[n+1][n+1] where all entries are initialized to -1, to store intermediate LCS results and avoid recomputation.

3. Define base case:
   If either string length becomes 0 during recursion (n1 == 0 or n2 == 0), return 0 as there is no subsequence possible.

4. Apply recursive relation:

   If characters s1[n1-1] and s2[n2-1] match, add 1 to result of subproblem lps(n1-1, n2-1).

   If not, take the max of lps(n1-1, n2) and lps(n1, n2-1).

5. Return final answer:
   The value dp[n][n] gives the length of the longest palindromic subsequence in the original string.
## Program:
```
/*
Program to implement to find the length of the longest palindromic subsequence in it.
Developed by: NAGINENI ROHITH
Register Number:  212222040105
*/
```
```
dp = [[-1 for i in range(1001)]for j in range(1001)]
def lps(s1, s2, n1, n2):
 
    if (n1 == 0 or n2 == 0):
        return 0
 
    if (dp[n1][n2] != -1):
        return dp[n1][n2]
 
    if (s1[n1 - 1] == s2[n2 - 1]):
        dp[n1][n2] = 1 + lps(s1, s2, n1 - 1, n2 - 1)
        return dp[n1][n2]
    else:
        dp[n1][n2] = max(lps(s1, s2, n1 - 1, n2), lps(s1, s2, n1, n2 - 1))
        return dp[n1][n2]
seq = input()
n = len(seq)
 
s2 = seq
s2 = s2[::-1]
print(f"The length of the LPS is {lps(s2, seq, n, n)}")

```
## Output:
![image](https://github.com/user-attachments/assets/34be4cb4-2f48-40aa-93d3-170d099ebfe7)


## Result:
Thus the program was executed successfully for finding the length of longest palindromic string.
