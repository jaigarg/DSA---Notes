#dsa #arrays
### [Set Matrix Zeroes](https://www.interviewbit.com/problems/set-matrix-zeros/)
? 
#### Explanation

This is classic question where we need to find a solution in place i.e. in constant space complexity. Here, we first identify if there are any zero in first row and column. Then, we check for all the elements in the inner matrix i.e. excluding the first row and column. If we find any zero, we mark the first element in the respective row and column as zero. Thus, once we are done, we iterate over the matrix again and if we find the first element in either row or column zero, we mark that element as zero as well. Now, for the first row and column, we maintain one boolean variable for each. If we have any of those true, we mark the entire first row or column or both as zeroes accordingly.
#### Solution

```cpp
void Solution::setZeroes(vector<vector<int>> &A) {
    int n = A.size();
    int m = A[0].size();

    bool hasZeroFirstRow = false;
    bool hasZeroFirstCol = false;

    // Check first row
    for (int j = 0; j < m; j++) {
        if (A[0][j] == 0) {
            hasZeroFirstRow = true;
            break;
        }
    }

    // Check first column
    for (int i = 0; i < n; i++) {
        if (A[i][0] == 0) {
            hasZeroFirstCol = true;
            break;
        }
    }

    // Use first row and col as flags
    for (int i = 1; i < n; i++) {
        for (int j = 1; j < m; j++) {
            if (A[i][j] == 0) {
                A[i][0] = 0;
                A[0][j] = 0;
            }
        }
    }

    // Set cells to 0 based on markers
    for (int i = 1; i < n; i++) {
        for (int j = 1; j < m; j++) {
            if (A[i][0] == 0 || A[0][j] == 0) {
                A[i][j] = 0;
            }
        }
    }

    // Zero out first column if needed
    if (hasZeroFirstCol) {
        for (int i = 0; i < n; i++) {
            A[i][0] = 0;
        }
    }

    // Zero out first row if needed
    if (hasZeroFirstRow) {
        for (int j = 0; j < m; j++) {
            A[0][j] = 0;
        }
    }
}
```

#### Complexity

- Time Complexity: O(nm)
- Space Complexity: O(1)