#dsa #arrays #maths #voting #candidate
### [N3 Repeat Number](https://www.interviewbit.com/problems/n3-repeat-number/)
? 
#### Explanation

This question is based on application of [[Moore's Voting Algorithm]]. It requires us to find the two candidates who can have frequency greater than N/3. After finding the candidates, we just check their frequencies to check whether there count is indeed greater than N/3 or not. 

Note: Moore's Voting Algorithm itself doesn't provide the count or the winning candidate, it only provides the best possible candidate who can be checked further. 
#### Solution

```cpp
int Solution::repeatedNumber(const vector<int> &A) {
    int first = INT_MIN, second = INT_MIN;
    int count1 = 0, count2 = 0;
    
    for(int num : A) {
        if(num == first) {
            count1++;
        } else if(num == second) {
            count2++;
        } else if(count1 == 0) {
            first = num;
            count1 = 1;
        } else if(count2 == 0) {
            second = num;
            count2 = 1;
        } else {
            count1--;
            count2--;
        }
    }

    count1 = count2 = 0;
    for(int num : A) {
        if(num == first) count1++;
        else if(num == second) count2++;
    }

    if(count1 > A.size()/3) return first;
    if(count2 > A.size()/3) return second;
    return -1;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)