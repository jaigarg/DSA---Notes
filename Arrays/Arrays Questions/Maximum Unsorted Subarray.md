#dsa #arrays #2Pointer 
### [Maximum Unsorted Subarray](https://www.interviewbit.com/problems/maximum-unsorted-subarray/)
? 
#### Explanation

This is a good question to understand if sorting is required or not. Here, we don't apply sorting directly. Instead, we cleverly find the first and last occurrence where `A[i] > A[i+1]`. Then we find the maximum and the minimum element in this interval from start to end. Then, all elements from left smaller than minimum element and all elements from right greater than maximum element are already sorted. We just need to sort the middle part. Hence, we return the array containing the two indices as `{unsorted_subarray_start, sorted_subarray_start}`
#### Solution

```cpp
vector<int> Solution::subUnsort(vector<int> &A)
{
    int start = -1, end = -1;
    int n = A.size();

    // Find initial disorder from the left
    for (int i = 0; i < n - 1; i++) {
        if (A[i] > A[i + 1]) {
            start = i;
            break;
        }
    }

    // Already sorted
    if (start == -1)
        return {-1};

    // Find initial disorder from the right
    for (int i = n - 1; i > 0; i--) {
        if (A[i] < A[i - 1]) {
            end = i;
            break;
        }
    }

    // Find min and max in the unsorted subarray
    int minElem = INT_MAX, maxElem = INT_MIN;
    for (int i = start; i <= end; i++) {
        minElem = min(minElem, A[i]);
        maxElem = max(maxElem, A[i]);
    }
    
    // Extend the start index to include any number > minElem
    while (start > 0 && A[start - 1] > minElem)
        start--;
        
    // Extend the end index to include any number < maxElem
    while (end < n - 1 && A[end + 1] < maxElem)
        end++;

    return {start, end};
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)