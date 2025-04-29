# EX 3D Pattern Matching
## DATE:29.04.25
## AIM:
To write a python program to implement pattern matching on the given string using Brute Force algorithm.

## Algorithm
1. Let the text be T of length n, and the pattern be P of length m.

2. Start from the first character of the text and check for a match with the pattern:
   - Compare P[0] with T[0], P[1] with T[1], and so on.

3. If all characters of the pattern match with the corresponding characters in the text, return the starting index of the match.

4. If a mismatch occurs, shift the pattern by one position to the right and repeat the comparison from the beginning of the pattern.

5. Continue this process until either a match is found or the entire text has been checked (i.e., when n - m + 1 comparisons have been made).

## Program:
```
/*
Program to implement the Pattern Matching.
Developed by: sreeja.v
Register Number:212222230169  
*/
def BF(s1,s2):
    ##############  Add your code here #############
    m=len(s1)
    n=len(s2)
    for i in range(m-n+1):
        j=0
        while j<n and s1[i+j]==s2[j]:
            j+=1
        if j==n:
            return i
    return -1
if __name__ == "__main__":
    a1=input() 
    a2=input() 
    b=BF(a1,a2)
    print(b)

```

## Output:
![Screenshot 2025-04-29 141817](https://github.com/user-attachments/assets/a9ff4c83-d5d0-4a1b-ae11-e96299b3b7cd)



## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
