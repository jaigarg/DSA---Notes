#dsa #arrays 
### [Partitions](https://www.interviewbit.com/problems/partitions/)
? 
#### Explanation

Just need to determine the total sum and points where the running sum equals to one-third and two-third of the total sum. At any given point, if running sum is equal to two-third of total sum, then it can be used for exactly the number of times the sum was equal to one-third of total sum till that point. Looking at the solution would provide much more clarity.
#### Solution

```cpp
int Solution::solve(int A, vector<int> &B) {

int sum = 0;

for(int i = 0; i<A; i++)
{
	sum += B[i];	
}
	
if(sum%3)
{
	return 0;
}

int oneThird = sum/3;
int twoThird = 2*(sum/3);

int possibleOneThird = 0;
int curSum = 0;

int ans = 0;

for(int i = 0; i<A-1; i++)

{
	curSum += B[i];
	
	if(curSum == twoThird)	
	{
		ans += possibleOneThird;
	}
	
	if(curSum == oneThird)
	{
		possibleOneThird++;
	}

}

return ans;

}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)