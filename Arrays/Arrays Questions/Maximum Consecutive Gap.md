#dsa #arrays #bucketing #pigeonhole
### [Maximum Consecutive Gap](https://www.interviewbit.com/problems/maximum-consecutive-gap/)
? 
#### Explanation

This question is prime application of bucketing where we create n-1 buckets ranging from minimum and maximum element in the given array. We find the minimum and maximum element falling in each bucket. Now, the maximum consecutive gap will exist in following conditions:
1. between the minimum element of array and minimum element of first bucket
2. between the maximum element of previous bucket and minimum element of current bucket
3. between the maximum element of last bucket and maximum element of the array.
#### Solution

```cpp
int Solution::maximumGap(const vector<int> &A) {
    int n = A.size();
    if (n < 2) return 0;

    int minElem = INT_MAX, maxElem = INT_MIN;
    for (int i = 0; i < n; i++) {
        minElem = min(minElem, A[i]);
        maxElem = max(maxElem, A[i]);
    }

    float delta = float(maxElem - minElem) / (n - 1);
    vector<int> min_bucket(n - 1, INT_MAX);
    vector<int> max_bucket(n - 1, INT_MIN);

    for (int i = 0; i < n; i++) {
        if (A[i] == minElem || A[i] == maxElem) continue;
        int index = floor((A[i] - minElem) / delta);
        min_bucket[index] = min(min_bucket[index], A[i]);
        max_bucket[index] = max(max_bucket[index], A[i]);
    }

    int prev = minElem, maxDiff = INT_MIN;
    for (int i = 0; i < n - 1; i++) {
        if (min_bucket[i] == INT_MAX) continue;
        maxDiff = max(maxDiff, min_bucket[i] - prev);
        prev = max_bucket[i];
    }

    maxDiff = max(maxDiff, maxElem - prev);
    return maxDiff;
}```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)