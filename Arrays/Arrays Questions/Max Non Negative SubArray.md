#dsa #arrays 
### [Max Non Negative SubArray](https://www.interviewbit.com/problems/max-non-negative-subarray/)
? 
#### Explanation

Need to compute and maintain the sum and length of each subarray, and thus finally finding the final subarray with maximum sum, maximum length and minimum starting index. This is good example to understand how to write clean code, when we have just have to do bruteforce and doesn't necessarily have a complex algorithm involved. 
Note: Use long long for maintaining sum to avoid overflow.
#### Solution

```cpp
vector<int> Solution::maxset(vector<int> &A) {

    int n = A.size();

    int startInd = 0;

    int maxLen = 0;

    long long maxSum = 0;

  

    for(int i = 0; i<n; i++) {

        long long sum = 0;

        int len = 0;

        int sInd = 0;

  

        if(A[i] >= 0) {

            sInd = i;

            while(i < n && A[i] >= 0) {

                sum += A[i];

                len++;

                i++;

            }

            if(sum > maxSum || (sum == maxSum && len > maxLen)) 
            {

                startInd = sInd;

                maxLen = len;

                maxSum = sum;

            } 

        }

    }

  

    vector<int> res;

    for(int i = startInd; i < startInd + maxLen; i++) {

        res.push_back(A[i]);

    }

    return res;

}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)