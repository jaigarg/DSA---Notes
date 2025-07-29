#dsa #arrays #greedy #intervals
### [Merge Intervals](https://www.interviewbit.com/problems/merge-intervals/)
? 
#### Explanation

This is a question where basic intuition just need to be implemented. It involves a greedy approach, where we divided the given intervals in three portions: 

1. Intervals before new Interval (cur_Interval.end < new_Interval.start)
2. Intervals overlapping with new Interval (cur_Interval.start <= new_Interval.end)
3. Intervals after new Interval (cur_Interval.start > new_Interval.end)

Now, (1) & (3) can directly be pushed into resultant intervals list, but we need to remove/merge the intervals in (2).

Merging can be done simply by taking the minimum of newInterval.start and all the intervals.start in (2) and maximum of newInterval.end and all the intervals.end in (2). Once all intervals are merged, resultant interval can be pushed to resultant intervals list.
#### Solution

```cpp
vector<Interval> Solution::insert(vector<Interval> &intervals, Interval newInterval) {

vector<Interval> res;

int n = intervals.size();

int i = 0;

while(i < n && intervals[i].end < newInterval.start)
{

	res.push_back(intervals[i]);
	i++;

}

while(i < n && intervals[i].start <= newInterval.end)
{

	newInterval.start = min(intervals[i].start, newInterval.start);
	newInterval.end = max(intervals[i].end, newInterval.end);
	i++;

}

res.push_back(newInterval);

while(i < n)
{

	res.push_back(intervals[i]);
	i++;

}

return res;

}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)