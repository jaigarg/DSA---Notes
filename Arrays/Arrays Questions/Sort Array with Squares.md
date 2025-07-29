#dsa #arrays #2Pointer #sort
### [Sort Array with Squares](https://www.interviewbit.com/problems/sort-array-with-squares/)
? 
#### Explanation

We need to create a resultant array in linear time thus, rulling out the possibility of sorting the given array. We use two pointer technique with one pointer at each end of given array. We add the square of the value pointed by the pointer whose absolute value in given array is maximum.
#### Solution

```cpp
vector<int> Solution::solve(vector<int> &A) {
    int n = A.size();
    int i = 0, j = n - 1, k = n - 1;
    vector<int> res(n, 0);

    while (i <= j) {
        if (abs(A[i]) > abs(A[j])) {
            res[k--] = A[i] * A[i];
            i++;
        } else {
            res[k--] = A[j] * A[j];
            j--;
        }
    }

    return res;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)