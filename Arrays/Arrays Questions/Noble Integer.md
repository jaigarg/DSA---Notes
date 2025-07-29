#dsa #arrays #sort 
### [Noble Integer](https://www.interviewbit.com/problems/noble-integer/)
? 
#### Explanation

This question requires to sort the array and traverse to find elements where 
`A[i] = n - i - 1`

Keep in mind to handle duplicates. Thus, meaning `3, 3, 3, 3` would return -1.
#### Solution

```cpp
int Solution::solve(vector<int> &A) {
    int n = A.size();
    sort(A.begin(), A.end());

    for (int i = 0; i < n; i++) {
        // Skip duplicates
        while (i + 1 < n && A[i] == A[i + 1]) {
            i++;
        }

        // If A[i] == count of elements strictly greater than A[i]
        if (A[i] == n - i - 1) {
            return 1;
        }
    }

    return -1;
}
```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity: O(1)