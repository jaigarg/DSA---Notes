#dsa #arrays #hashMap
### [Occurence of each Element](https://www.interviewbit.com/problems/occurence-of-each-number/)
? 
#### Explanation

This is standard question requiring use of map. We just simply use a map to get the frequency of each element and then iterate over the same to get the final frequencies back.
#### Solution

```cpp
vector<int> Solution::findOccurences(vector<int> &A) {

vector<int> res_vec;
map<int, int> freq;

for(int i = 0; i<A.size(); i++)
{
	freq[A[i]]++;
}

for(map<int, int>::iterator itr = freq.begin(); itr != freq.end(); itr++)
{
	res_vec.push_back(itr->second);
}

return res_vec;
}
```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity: O(n)