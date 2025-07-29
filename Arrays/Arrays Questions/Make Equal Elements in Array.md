#dsa #arrays #hashMap #sort 
### [Make Equal Elements in Array](https://www.interviewbit.com/problems/make-equal-elements-array/)
? 
#### Explanation

This can be solved in two ways:
1. Sorting and then checking the sum of differences between consecutive elements.
2. Using an unordered_map to store all the possible elements after operations and checking final count.
First approach is more elegant, where we check the condition that the sum of differences between consecutive elements should never be not divisible by B. If that happens, we will never be able to make those two elements equal, meaning that if `A[i] - A[i-1]` is not divisible by B, then, `A[i]` will never be equal to `A[i-1]` regardless of the operation we perform using B.
#### Solution

```cpp
//Code - 1 (Sorting + Sum of differences)
int Solution::solve(vector<int> &A, int B) {

sort(A.begin(), A.end());

int sum = 0;

for(int i = 1; i<A.size(); i++)
{
	sum = sum + A[i]-A[i-1];
	
	if((sum%B > 0) || (sum>2*B))	
	{
		return 0;
	}
}

return 1;
}

//Code - 2 (Unordered_map + Count occurences)
int Solution::solve(vector<int> &A, int B) {

unordered_map<int, int> umap;

int n = A.size();

for(int i = 0; i<n; i++)
{
	umap[A[i]]++;
	umap[A[i] + B]++;
	umap[A[i] - B]++;
}

for(auto val: umap)
{
	if(val.second == n)
	{
		return 1;
	}
}

return 0;
}
```

#### Complexity

- Time Complexity: 
	- Code: 1 - O(nLogn)
	- Code: 2 - O(n)
- Space Complexity: 
	- Code: 1 - O(1)
	- Code: 2 - O(n)