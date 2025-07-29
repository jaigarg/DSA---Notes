#dsa #arrays #2Pointer
### [Move Zeros](https://www.interviewbit.com/problems/move-zeroes/)
? 
#### Explanation

Simple yet eleganto!! Need to understand how to simplify the requirement and then solve this one. Basically all non-zero need to be brought in front of all zeros. So, we just shift them by maintaining two pointers both starting from 0. Once we are done with all non-zeros, we set the rest of the values as zeros.
#### Solution

```cpp
vector<int> Solution::solve(vector<int> &A) {

int n = A.size();
int j = 0;
int i = 0;

while(i < n)
{
	if(A[i] != 0)
	{
		A[j++] = A[i];
	}
	i++;
}

while(j<n)
{
	A[j] = 0;
	j++;
}

return A;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)