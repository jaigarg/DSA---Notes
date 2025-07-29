#dsa #arrays #kadane
### [Flip](https://www.interviewbit.com/problems/flip/)
? 
#### Explanation

This question involves a subtle modification of [[Kadane's Alogrithm]] where we treat every '0' as 1 and every '1' as -1 for calculating maximum sum contiguous subarray. Here, the maximum sum gives us the subarray, which has maximum '0's and minimizes the loss of '1's during flipping process.
#### Solution

```cpp
vector<int> Solution::flip(string A) {
    int curSum = 0;
    int maxSum = 0;
    int st = 0;
    int lInd = -1, rInd = -1;
    int n = A.size();
    
    for(int i = 0; i < n; i++) {
        if(curSum < 0) {
            if(A[i] == '0') {
                curSum = 1;
            } else {
                curSum = -1;
            }
            st = i;
        } else {
            if(A[i] == '0') {
                curSum += 1;
            } else {
                curSum -= 1;
            }
        }
        
        if(maxSum < curSum) {
            maxSum = curSum;
            lInd = st;
            rInd = i;
        }
    }
    
    if(lInd == -1) {
        return {};
    } else {
        return {lInd + 1, rInd + 1};
    }
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)