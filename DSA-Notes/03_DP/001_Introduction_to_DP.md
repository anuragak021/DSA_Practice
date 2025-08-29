# Introduction to DP


## Problem Statement

Geek is learning data structures, and he recently learned about the top-down and bottom-up dynamic programming approaches. Geek is having trouble telling them apart from one another.

When given an integer n, where n is based on a 0-based index, find the nth Fibonacci number.

Every ith number in the series equals the sum of the (i-1)th and (i-2)th numbers, where the first and second numbers are specified as 0 and 1, respectively.

For the given issue, code both top-down and bottom-up approaches.

Note : As the answer might be large, return the final answer modulo 109 + 7

### example test cases

Example 1:

Input:
n = 5
Output: 5
Explanation: 0,1,1,2,3,5 as we can see 5th number is 5.
Example 2:

Input:
n = 6
Output: 8
Explanation: 0,1,1,2,3,5,8 as we can see 6th number is 8.
Constraints:
1 <= n <= 10^4
Your Task:
You don't need to read input or print anything. Your task is to complete two functions topDown() and bottomUp() which take n as input parameters and return the nth Fibonacci number.

Expected Time Complexity: O(n)
Expected Auxiliary Space: O(n)

---
## 💡 Approaches

### 📌 Best Approach 
Initialize three variables named prev2 , prev and curi . Take prev2 = 0 , prev = 1 and take curi as empty . Iterate on a loop from i = 2 ; to i <= n , and give the value of curi = prev + prev2 , prev2 = prev and prev = curi. At last print prev.
#### Code (C++)
```cpp
    const int MOD = 1e9 + 7 ;
    long long int topDown(int n) {
        // code here
        int curi = 0 ; 
        int prev2 = 0  , prev = 1 ;
        for(int i = 2 ; i <= n ; ++i){
            curi = (prev2 + prev) %  MOD;
            prev2 = prev ;
            prev = curi;
        }
        return prev % MOD;
        
    }
```
#### TC and SC
- **Time Complexity:** O(N)
- **Space Complexity:** O(1)

---

### Approach 1
MEMOIZATION / TOP DOWN DP: Every time a problem is solved store it then return it. 
<br>
dp[n]= [-1 , -1 , -1 , -1 , -1]
<br>
After let's say n = 5 <br>
dp[n]=[-1 , -1 , 1 ,2 , 3, 5]
<br>
In the recursion just have a base case then if(dp[n] != -1 ) return dp[n];
<br>
else return dp[n]= func(n-1 , dp) + func(n-2 , dp);
#### Code (C++)
```cpp
    const int MOD = 1e9 + 7 ;
    long long int solve(int n , vector<int> &dp){
        if(n <= 1)  return n;
        if(dp[n] != -1) return (dp[n]) % MOD;
        return dp[n] = (solve(n-1 , dp) + solve(n-2 , dp)) % MOD;
    }
    
    long long int topDown(int n) {
        // code here
        vector<int> dp(n+1 , -1);
        return solve(n , dp);
    }
```
#### TC and SC
- **Time Complexity:** O(N)
- **Space Complexity:** O(N)+ O(N)

---

### Approach 2
TABULATION / BOTTOM UP DP: Here we will go from base case to the required . First Initialise the dp and set the base cases . Then run a for loop from i = 2 ; i <= n , and compute the value of each using dp[i] = dp[i-1] + dp[i-2]. 
#### Code (C++)
```cpp
    long long int bottomUp(int n) {
        vector<int> dp(n+1 , -1);
        dp[0] = 0  , dp[1] = 1;
        for(int i = 2 ; i <= n ; ++i){
            dp[i] = (dp[i-2] + dp[i-1]) % MOD;
        }
        return dp[n];
    }
```
#### TC and SC
- **Time Complexity:**O(N) 
- **Space Complexity:**O(N) 

---

## 📝 Notes
Best method for fibonacci : O(log n) -> CP Algorithms and CSES math problem