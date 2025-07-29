#dsa #arrays #set
### [Maximum Sum Triplet](https://www.interviewbit.com/problems/maximum-sum-triplet/)
? 
#### Explanation

This question requires good use of how to use data structures effectively. In this question, we assume each number to be the middle number of the triplet and try to find the smaller one on the left and greater one on the right. For finding smaller number on left, we use a set, which contains all the numbers traversed so far, and thus enabling us to utilize the lower_bound functionality to find the smaller number required. Similarly, for the greater number on right, we maintain a suffixMax array, which contains the maximum number encounter from right side for each index. Thus, if we want to find the possible answer for a given index i,

```cpp
Smaller_number_on_left = *(--set.lower_bound(A[i]);
Greater_number_on_right = suffixMax[i+1];
```

#### Solution

```cpp
int Solution::solve(vector<int> &A) {

int n = A.size();

int res = 0;

vector<int> suf_max(n + 1, 0);

for(int i = n-1; i>=0; i--)

{

	suf_max[i] = max(suf_max[i+1], A[i]);

}

set<int> low_bnd;

low_bnd.insert(INT_MIN);

low_bnd.insert(A[0]);

for(int i = 1; i<n-1; i++)

{

	int low_val = 0;
	
	if(suf_max[i+1] > A[i])
	
	{
	
		low_val = *(--(low_bnd.lower_bound(A[i])));
	
		if(low_val != INT_MIN)
		
		{
		
			res = max(res, low_val + A[i] + suf_max[i+1]);
		
		}
	
	}
	
	low_bnd.insert(A[i]);

}

return res;

}
```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity: O(n)