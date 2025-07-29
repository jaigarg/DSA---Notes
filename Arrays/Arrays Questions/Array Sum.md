#dsa #arrays 
### [Array Sum](https://www.interviewbit.com/problems/array-sum/hints/)
? 
#### Explanation

Simple sum all each element till the length of first array is exhausted, then take the second array along with any leftover carry. Not necessary to do in place.
#### Solution

```cpp
vector<int> Solution::addArrays(vector<int> &A, vector<int> &B) {

int n = A.size();
int m = B.size();

if(n > m)
{
	return addArrays(B, A);
}

int i = n-1, j = m-1;
int carry = 0;

while(i>=0)
{
	int num = (A[i] + B[j] + carry);
	B[j] = num%10;
	carry = num/10;
	i--;
	j--;
}

while(j>=0)
{
	int num = (B[j] + carry);
	B[j] = num%10;
	carry = num/10;
	j--;
}

while(carry)
{
	B.insert(B.begin(), carry%10);
	carry /= 10;
}

return B;

}
```

#### Complexity

- Time Complexity: O(max(n, m))
- Space Complexity: O(1) (if in place, otherwise O(max(n, m)))