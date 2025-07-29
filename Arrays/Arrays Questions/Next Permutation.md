#dsa #arrays #permutation #greedy 
### [Next Permutation](https://www.interviewbit.com/problems/next-permutation/)
? 
#### Explanation

This question requires us to find the just the next permutation of the given array number. Now, we need to make changes from right hand side to ensure it is the smallest jump from give number. So, we find the first element from right which is smaller than the element on it right. This is the position that needs to be updated with the smallest element on right to form the next permutation. Once the swap is done, we just need to reverse the leftover part to get it sort in ascending order.
#### Solution

```cpp
vector<int> Solution::nextPermutation(vector<int> &A) {
    int n = A.size();
    int pivotInd = n - 1;

    // Step 1: Find the pivot
    while (pivotInd > 0 && A[pivotInd - 1] >= A[pivotInd]) {
        pivotInd--;
    }

    // Step 2: If a valid pivot is found
    if (pivotInd > 0) {
        for (int i = n - 1; i >= pivotInd; i--) {
            if (A[pivotInd - 1] < A[i]) {
                swap(A[i], A[pivotInd - 1]);
                break;
            }
        }
    }

    // Step 3: Reverse the suffix
    reverse(A.begin() + pivotInd, A.end());

    return A;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)