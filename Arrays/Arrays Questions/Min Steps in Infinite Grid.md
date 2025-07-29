#dsa #arrays #greedy 
### [Min Steps in Infinite Grid](https://www.interviewbit.com/problems/min-steps-in-infinite-grid/l)
? 
#### Explanation

Just understand the best way of going from one point to any other point. Suppose we are going from (x1, y1) to (x2, y2). Then, the best way to reach (x2, y2) is to go in the diagonal direction as much as possible to minimize steps. Then, we will reach a point where we will reach a condition where either x1 = x2 or y1 = y2. Now, we only need to go vertically or horizontally to reach (x2, y2). So, in essence we just need to take the max(abs(x2 - x1), abs(y2 - y1)) steps. 
#### Solution

```cpp
int Solution::coverPoints(vector<int> &A, vector<int> &B) {

	int n = A.size();
	int steps = 0;
	for(int i = 1; i<n; i++)
	{
		steps += max(abs(A[i] - A[i-1]), abs(B[i] - B[i-1]));
	}
	
	return steps;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)