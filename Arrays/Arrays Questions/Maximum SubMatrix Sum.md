#dsa #arrays 
### [Maximum SubMatrix Sum](https://www.interviewbit.com/problems/maximum-sum-square-submatrix/)
? 
#### Explanation

In this question, we preprocess the matrix and create a sum matrix where we store the sum till each element in the matrix. Then, we iterate over all possible `B*B` matrices to find the maximum sum amongst them.
#### Solution

```cpp
int Solution::solve(vector<vector<int>> &A, int B) {
    int n = A.size();
    vector<vector<int>> sumMat(n, vector<int>(n, 0));

    // Build sum matrix (prefix sum matrix)
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            sumMat[i][j] = A[i][j];
            if(i > 0) sumMat[i][j] += sumMat[i - 1][j];
            if(j > 0) sumMat[i][j] += sumMat[i][j - 1];
            if(i > 0 && j > 0) sumMat[i][j] -= sumMat[i - 1][j - 1];
        }
    }

    int maxSum = INT_MIN;
    for(int i = B - 1; i < n; i++) {
        for(int j = B - 1; j < n; j++) {
            int total = sumMat[i][j];
            if(i - B >= 0) total -= sumMat[i - B][j];
            if(j - B >= 0) total -= sumMat[i][j - B];
            if(i - B >= 0 && j - B >= 0) total += sumMat[i - B][j - B];
            maxSum = max(maxSum, total);
        }
    }

    return maxSum;
}
```

#### Complexity

- Time Complexity: O(n<sup>2</sup>)
- Space Complexity: O(n<sup>2</sup>)