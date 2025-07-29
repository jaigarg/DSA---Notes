#dsa #arrays #2Pointer 
### [Max Distance](https://www.interviewbit.com/problems/max-distance/)
? 
#### Explanation

This question requires use of suffix max array in order to have the maximum element to the right of each element. We then use a two pointer approach, where we place one pointer at the start of given array and another at the start of suffix max array. Now, we increment 2nd pointer pointing to suffix max as long as the maximum element to the right of current element is greater while calculating the maximum difference between the elements. Once, we don't have suffix max array element larger than current element, we increment 1st pointer pointing to given array.
#### Solution

```cpp
int Solution::maximumGap(const vector<int> &A) {
    int n = A.size();
    int maxGap = 0;
    vector<int> suffMax(n, INT_MIN);
    suffMax[n-1] = A[n-1];

    for(int i = n-2; i >= 0; i--) {
        suffMax[i] = max(suffMax[i+1], A[i]);
    }

    int i = 0, j = 0;

    while(i < n && j < n) {
        if(A[i] <= suffMax[j]) {
            maxGap = max(maxGap, j - i);
            j++;
        } else {
            i++;
        }
    }

    return maxGap;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)