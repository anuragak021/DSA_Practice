# 08 2025 Count Square Submatrices with All Ones

### ### Problem [Link](https://leetcode.com/problems/count-square-submatrices-with-all-ones/)

## Problem Statement

[Given a m * n matrix of ones and zeros, return how many square submatrices have all ones.]

### example test cases

Example 1:

Input: matrix =
[
  [0,1,1,1],
  [1,1,1,1],
  [0,1,1,1]
]
Output: 15
Explanation: 
There are 10 squares of side 1.
There are 4 squares of side 2.
There is  1 square of side 3.
Total number of squares = 10 + 4 + 1 = 15.
Example 2:

Input: matrix = 
[
  [1,0,1],
  [1,1,0],
  [1,1,0]
]
Output: 7
Explanation: 
There are 6 squares of side 1.  
There is 1 square of side 2. 
Total number of squares = 6 + 1 = 7.
Constraints:

1 <= arr.length <= 300
1 <= arr[0].length <= 300
0 <= arr[i][j] <= 1

---
## 💡 Approaches

### 📌 Best Approach 
[Take the matrix from every length and then take it's next , diagonal and bottom one]

#### Code (C++)
```cpp
// [PASTE_YOUR_BEST_APPROACH_CODE_SOLUTION_HERE]
class Solution {
public:
    int n, m;
    int solve(int i, int j, vector<vector<int>>& matrix,
              vector<vector<int>>& t) {
        if (i >= m || j >= n) {
            return 0;
        }
        if (matrix[i][j] == 0) {
            return 0;
        }
        if(t[i][j] != -1){
            return t[i][j];
        }
        int right = solve(i, j + 1, matrix, t);
        int diag = solve(i + 1, j + 1, matrix, t);
        int below = solve(i + 1, j, matrix, t);
        return t[i][j] = 1 + min({right, diag, below});
    }
    int countSquares(vector<vector<int>>& matrix) {
        m = matrix.size();
        n = matrix[0].size();
        int result = 0;
        vector<vector<int>> t(m + 1, vector<int>(n + 1, -1));
        //TC = O(m * n)
        //SC = O(m*n)
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (matrix[i][j] == 1) {
                    result += solve(i, j, matrix, t);
                }
            }
        }
        return result;
    }
};

```
#### TC and SC

- **Time Complexity:** [O(m*n)]
- **Space Complexity:** [O(m*n)]

---

### Approach 1
[EXPLAIN_APPROACH_1_LOGIC_HERE]
#### Code (C++)
```cpp
// [PASTE_CODE_FOR_APPROACH_1_HERE]

```
#### TC and SC
- **Time Complexity:** [ADD_TIME_COMPLEXITY_HERE]
- **Space Complexity:** [ADD_SPACE_COMPLEXITY_HERE]

---

### Approach 2
[EXPLAIN_APPROACH_2_LOGIC_HERE]
#### Code (C++)
```cpp
// [PASTE_CODE_FOR_APPROACH_2_HERE]

```
#### TC and SC
- **Time Complexity:** [ADD_TIME_COMPLEXITY_HERE]
- **Space Complexity:** [ADD_SPACE_COMPLEXITY_HERE]

---

## 📝 Notes

[ADD_ANY_ADDITIONAL_NOTES_OR_KEY_TAKEAWAYS_HERE]
