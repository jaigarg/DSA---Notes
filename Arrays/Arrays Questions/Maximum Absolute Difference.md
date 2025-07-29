#dsa #arrays #greedy
### [Maximum Absolute Difference](https://www.interviewbit.com/problems/maximum-absolute-difference/)
? 
#### Explanation

This question involves simplifying the required condition, i.e. 
```
|A[i] - A[j]| + |i - j| 
```

If you look carefully, this condition can be resolved only in two ways ultimately:
```
1. (A[i] + i) - (A[j] - j)
2. (A[i] - i) - (A[j] - j)
```

In both cases, we need to maximize the first term and minimize the second term to get the absolute maximum difference.
#### Solution

```cpp
int Solution::maxArr(vector<int> &A) {

int c1_max = INT_MIN;
int c1_min = INT_MAX;
int c2_max = INT_MIN;
int c2_min = INT_MAX;

for(int i = 0; i<A.size(); i++)

{

	c1_max = max(c1_max, A[i] + i);
	c1_min = min(c1_min, A[i] + i);
	c2_max = max(c2_max, A[i] - i);
	c2_min = min(c2_min, A[i] - i);

}

return max(c1_max - c1_min, c2_max - c2_min);

}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity:  O(1)