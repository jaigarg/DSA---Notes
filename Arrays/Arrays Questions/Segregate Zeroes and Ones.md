#dsa #arrays 
### [Segregate Zeroes and Ones](https://www.interviewbit.com/problems/segregate-0s-and-1s-in-an-array/hints/)
? 
#### Explanation

In this question, we can simply count number of zeros (numZeros) and then create an array of ones of same size and set starting numZeros elements as zero.
Another elegant approach can be to do all this in one traversal, by maintaining a separate pointer in new array of ones. 
If required to do in place, then just do traversal to put all zeros at beginning and then setting all subsequent elements as one.
#### Solution

```cpp
vector<int> Solution::solve(vector<int> &A) {

int j = 0;

int i = 0;

int n = A.size();

vector<int> B(n, 1);

while(i < n)
{
	if(A[i] == 0)
	{
		B[j++] = 0;
	}
	i++;
}

return B;

}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)