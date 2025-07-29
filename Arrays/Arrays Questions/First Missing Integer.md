#dsa #arrays 
### [First Missing Integer](https://www.interviewbit.com/problems/first-missing-integer/)
? 
#### Explanation

In this question, we place the positive integers in the given array in their correct position based on ascending order (in place). Then, we iterate over the given array and the return the first number we encounter with condition `A[i] != i+1`. In case, we don't find any element in array with this property, then we simply return `n+1`
#### Solution

```cpp
int Solution::firstMissingPositive(vector<int> &A) {

	int n = A.size();
	
	for(int i = 0; i<n; i++)
	{
		if(A[i] > 0 && A[i] <= n)
		{
			int pos = A[i] - 1;
			if(A[pos] != A[i])
			{
				swap(A[pos], A[i]);
				i--;
			}
		}
	}
	
	for(int i = 0; i<n; i++)
	{
		if(A[i] != i+1)
		{
			return i+1;
		}
	}
	
	return n+1;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)