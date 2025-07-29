#dsa #arrays #intervals #sort 
### [Merge Overlapping Intervals](https://www.interviewbit.com/problems/merge-overlapping-intervals/)
? 
#### Explanation

This is standard overlapping intervals question. It requires sorting by the start times and then making sure to merge the overlapping intervals as we iterate over the sorted intervals list. If there is no interval overlapping at any point, we can push it to resultant intervals list. If there is overlap, then we update the next interval with start time of current interval and end time as maximum of current and next intervals end times.
#### Solution

```cpp
vector<Interval> Solution::merge(vector<Interval> &A) {

sort(A.begin(), A.end(), compIntervals);
vector<Interval> res;
int n = A.size();

for(int i = 0; i < n-1; i++)
{
	if(A[i].end >= A[i+1].start)
	{
		A[i+1].start = A[i].start;
		A[i+1].end = max(A[i+1].end, A[i].end);
	}
	
	else
	{
		res.push_back(A[i]);
	}

}

res.push_back(A.back());
return res;
}
```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity:  O(n)