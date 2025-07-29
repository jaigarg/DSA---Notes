#dsa #arrays #comparator #sort 
### [Largest Number](https://www.interviewbit.com/problems/largest-number/)
? 
#### Explanation

Just convert all the number to string and sort the newly formed string array using a custom comparator method where we check `string_a + string_b > string_b + string_a`
Then all values can be appended together to form the largest value.
#### Solution

```cpp
bool strComp(string a, string b) {
    return (a + b) > (b + a);
}

string Solution::largestNumber(const vector<int> &A) {
    vector<string> strA;
    string res = "";
    int zeroCnt = 0;

    for (auto val : A) {
        if (val == 0) zeroCnt++;
        strA.push_back(to_string(val));
    }

    if (zeroCnt == A.size()) return "0";

    sort(strA.begin(), strA.end(), strComp);

    for (auto val : strA) {
        res.append(val);
    }

    return res;
}
```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity: O(n)