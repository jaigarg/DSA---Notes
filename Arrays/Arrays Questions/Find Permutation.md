#dsa #arrays #2Pointer #permutation 
### [Find Permutation](https://www.interviewbit.com/problems/find-permutation/)
? 
#### Explanation

This is a really good question where two pointer approach can be leveraged to solve the problem elegantly. We set `l=1` and `r=n`, then, 
For `I`, we push `l` and increment it by one
For `D`, we push r and decrement it by one

This way, for every `I`, we push the smallest element available, so that no matter what is entered afterwards will always be bigger than the current one. Similarly for every `D`, we push the largest element available. 

Note: There are in total `n-1` operations being performed in which either `l` increases or `r` decreases. Thus, at the end `l==r`. We need to push either `l` or `r` to complete the sequence.
#### Solution

```cpp
vector<int> Solution::findPerm(const string A, int B) {
    int l = 1, r = B;
    int n = A.size();
    vector<int> res;

    for (int i = 0; i < n; i++) {
        if (A[i] == 'I') {
            res.push_back(l++);
        } else {
            res.push_back(r--);
        }
    }

    // Push the last remaining number
    res.push_back(r);
    return res;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)