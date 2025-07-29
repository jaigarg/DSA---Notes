#dsa #arrays
### [Perfect Peak of Array](https://www.interviewbit.com/problems/perfect-peak-of-array/)
? 
#### Explanation

This is tricky question. Read the question carefully. It asks for an element which is strictly greater of all elements on left and strictly smaller of all elements on right. If you look carefully, this not same as monotonic or biotonic array conditions. Basically, it doesn't matter what happens on right or left as long as there is an element that is strictly greater the left and smaller than right. 
For example: `5, 5, 5, 5, 8, 5, 5, 5, 5` would satisfy the condition.
#### Solution

```cpp
int Solution::perfectPeak(vector<int> &A) {

int n = A.size();
vector<int> premax(n, 0);
premax[0] = A[0];
int sufmin = A[n-1];

for(int i = 1; i<n; i++)
{
	premax[i] = max(premax[i-1], A[i]);
}

for(int i = n-2; i>0; i--)
{
	if(A[i] > premax[i-1] && A[i] < sufmin)
	{
		return 1;
	}
	
	sufmin = min(A[i], sufmin);
}

return 0;

}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)