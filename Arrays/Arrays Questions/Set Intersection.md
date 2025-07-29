#dsa #arrays #sort #comparator #intervals #greedy 
### [Set Intersection](https://www.interviewbit.com/problems/set-intersection/)
? 
#### Explanation

In this question, we sort the array according to their end times and then according to their start times. Then, we pick the last two values in the first interval, push to the set and check against the subsequent intervals interval. If the start value of next interval is greater than the last value of set, then we need to add end and end - 1 in the set. If the start value of next interval is greater than second last value of set, then we add the end of next interval in set. Otherwise, we don't need to add any values to set, since two elements of next interval are already included.

Note: Think about how we will form the set, if asked.
#### Solution

```cpp
static bool mycomp(const vector < int > & A, const vector < int > & B) {
	if (A[1] != B[1])
		return A[1] < B[1];
	return A[0] < B[0];
}

int intersectionSizeTwo(vector <vector<int>> &A) {
	int n = A.size();
	sort(A.begin(), A.end(), Solution::mycomp);
	vector < int > res;
	res.push_back(A[0][1] - 1);
	res.push_back(A[0][1]);
	
	for (int i = 1; i < n; i++) {
		int start = A[i][0];
		int end = A[i][1];
		int size = res.size();
		int last = res[size - 1];
		int secondLast = res[size - 2];
		
		if (start > last) {
			res.push_back(end - 1);
			res.push_back(end);
		}
		
		else if (start > secondLast) {
			if(last == end)
			{
				res.pop_back();
				res.push_back(end-1);
				res.push_back(end);
			}
			else res.push_back(end);
		}
	}
	
	return res.size();
}
```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity: O(n)