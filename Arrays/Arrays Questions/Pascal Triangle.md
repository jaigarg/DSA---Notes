#dsa #arrays 
### [Pascal Triangle](https://www.interviewbit.com/problems/pascal-triangle/)
? 
#### Explanation

This is a standard Pascal Triangle question, where we need to print the first K rows of the same. We simply use the property that every element is sum of the elements directly above in the previous row with exception of ones present at start and end of each row. 
#### Solution

```cpp
vector<vector<int> > Solution::solve(int A) {

vector<vector<int>> res;

if(A == 0)
{
	return res;
}

res.push_back({1});

for(int i = 1; i<A; i++)
{
	vector<int> temp;
	temp.push_back(1);
	
	for(int j = 1; j<res[i-1].size(); j++)
	{
		int num = res[i-1][j-1] + res[i-1][j];
		temp.push_back(num);
	}
	
	temp.push_back(1);
	res.push_back(temp);
}

return res;
}
```

#### Complexity

- Time Complexity: O(n^2)
- Space Complexity: O(n^2)