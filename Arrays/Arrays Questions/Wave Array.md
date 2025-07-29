#dsa #arrays #sort
### [Wave Array](https://www.interviewbit.com/problems/wave-array/)
? 
#### Explanation

Standard sorting question, where you sort and just swap adjacent elements
#### Solution

```cpp
vector<int> Solution::wave(vector<int> &A) {
    sort(A.begin(), A.end());
    int n = A.size();
    for(int i = 0; i < n - 1; i += 2) {
        swap(A[i], A[i + 1]);
    }
    return A;
}
```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity: O(1)