# EX 4D DYNAMIC PROGRAMMING – 4
## DATE:
## AIM:
To find the minimum number of operations to convert str1 to str2 using Naive recursive method.
## Algorithm
1. Base Case Handling:

   If the first string s is empty, return the length of t (all characters of t need to be inserted).

   If the second string t is empty, return the length of s (all characters of s need to be deleted).

2. Check Last Character Match:
   If the last characters of s and t are equal, set cost = 0. Otherwise, set cost = 1 (indicating a substitution is needed).

3. Recursive Operations:
   Compute three possibilities recursively:

   Insert: Edit distance of LD(s, t[:-1]) + 1

   Delete: Edit distance of LD(s[:-1], t) + 1

   Replace: Edit distance of LD(s[:-1], t[:-1]) + cost

4. Take Minimum of Three:
   Return the minimum of the above three computed values, representing the optimal operation.

5. Final Result:
   The function LD(str1, str2) returns the minimum number of operations (insertions, deletions, substitutions) to convert str1 into str2.   

## Program:
```
/*
Program to implement to find the minimum number of operations to convert str1 to str2 using Naive recursive method.
Developed by: NAGINENI ROHITH
Register Number: 212222040105 
*/
```
```
def LD(s, t):
    if s == "":
        return len(t)
    if t == "":
        return len(s)
    if s[-1] == t[-1]:
        cost = 0
    else:
        cost = 1
    res = min([LD(s[:-1], t)+1,
               LD(s, t[:-1])+1, 
               LD(s[:-1], t[:-1]) + cost])
    return res
    
str1=input()
str2=input()
print('Edit Distance',LD(str1,str2))


```
## Output:
![image](https://github.com/user-attachments/assets/7adab534-7a00-4c86-b4b2-05ce3234fa82)


## Result:
Thus the program was executed successfully for finding edit distance between two strings.
