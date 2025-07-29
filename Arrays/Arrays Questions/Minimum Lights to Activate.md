#dsa #arrays #greedy
### [Minimum Lights to Activate](https://www.interviewbit.com/problems/minimum-lights-to-activate/)
? 
#### Explanation

This question requires a greedy approach where we turn on the right most light possible to make sure we cover maximum distance towards right and thus, minimize the number of lights to be switched on. 
#### Solution

```cpp
int Solution::solve(vector<int> &A, int B) {

int numLights = 0;

int n = A.size();

int lightInd = 0;

while(lightInd < n)

{

	bool lightFound = false;
	
	for(int i = lightInd + B - 1; i >= 0 && i > lightInd - B; i--)
	
	{
	
		if(A[i])
		
		{
		
			lightFound = true;
			
			numLights++;
			
			lightInd = i + B;
			
			break;
		
		}
		
	}
		
	if(!lightFound)
	{
	
		return -1;
	
	}
}

return numLights;

}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)