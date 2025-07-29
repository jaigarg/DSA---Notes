#dsa #arrays #kadane 
### [Maximum Contiguous Subarray Sum](https://www.interviewbit.com/problems/max-sum-contiguous-subarray/)
? 
#### Explanation

This is a standard question of application of [[Kadane's Alogrithm]]. Here, we are applying simple Kadane's Algorithm which maintains a Current Sum and a Maximum Sum. Whenever current sum drops below zero, it is assigned the current element, otherwise current element is added. At every iteration, maximum sum is updated if less than current sum. 
#### Solution

```cpp
int Solution::maxSubArray(const vector<int> &A) {

int ms = A[0];
int cs = A[0];
int n = A.size();

for(int i = 1; i<n; i++)

{

	if(cs < 0)
	{
		cs = A[i];
	}
	
	else
	{
		cs += A[i];
	}
	
	if(cs > ms)
	{
		ms = cs;
	}

}

return ms;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)