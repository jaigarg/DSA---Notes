#dsa #arrays #strings
### [Large Factorial Number](https://www.interviewbit.com/problems/large-factorial/)
? 
#### Explanation

Use a vector to get the factorial value by multiplying the next number one by one and maintain the carry. Once all number till the given number is considered for multiplication, just append the reversed vector to the string to get the final factorial value.

#### Solution

```cpp

string Solution::solve(int A) {

vector<int> res_vec;

res_vec.push_back(1);

int carry = 0;

int prod = 0;

string res = "";

for(int i = 2; i<=A; i++) {

	for(int j = 0; j<res_vec.size(); j++) {
	
		int prod = (res_vec[j]*i + carry);
		
		res_vec[j] = prod%10;
		
		carry = prod/10;
	
	}
	
	while(carry) {
	
		res_vec.push_back(carry%10);
		
		carry /= 10;
	
	}

}

for(int i = res_vec.size() - 1; i>=0; i--) {

	res.push_back(res_vec[i] + '0');

}

return res;

}

```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity: O(n)