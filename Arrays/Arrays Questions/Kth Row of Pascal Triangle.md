#dsa #arrays #combinatorics
### [Kth Row of Pascal Triangle](https://www.interviewbit.com/problems/kth-row-of-pascals-triangle/)
? 
#### Explanation

This involves use of a Combinatorics where we can get the 
$C(N, r) = (C(N, r-1) * (N - r + 1))/r$   -> (1)

So, as we know Pascal Triangle's Kth row can be written as:

`C(K, 0) C(K, 1) C(K, 2) ........ C(K, K-2) C(K, K-1) C(K, K)`

And we know C(K, 0) = 1, thus using condition (1), we can get all subsequent C(K, i) and push to resultant vector.

For example: $C(A, i) = (C*(A-i+1))/i$
#### Solution

```cpp
vector<int> Solution::getRow(int A) {

vector<int> res_vec;
int val = 1;
res_vec.push_back(val);

for(int i = 1; i<=A; i++)
{
	val = (val*(A-i+1))/i;
	res_vec.push_back(val);
}

return res_vec;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(n)