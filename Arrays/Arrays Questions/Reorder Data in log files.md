#dsa #arrays #sort #comparator #strings
### [Reorder Data in log files](https://www.interviewbit.com/problems/reorder-data-in-log-files/)
? 
#### Explanation

This is a very question to understand comparators for sorting. Here, we have conditions where we need to sort according to log type, log content and log header. We separate out the letter and digit logs and sort the letter logs according to given requirements. Then we merge them together to form the resultant log array.

Note: We can do all this in a single comparator method as well. Please check second solution as well. Understand how we handle cases where we want to retain the existing order and use of stable_sort.
#### Solution

```cpp
bool mycompare(pair<string, string> p1, pair<string, string> p2)
{
    if (p1.second == p2.second)
        return p1.first < p2.first;
    return p1.second < p2.second;
}

vector<string> Solution::reorderLogs(vector<string> &A) {
    vector<string> res_vec;
    vector<pair<string, string>> letter;
    vector<string> digit;

    for (int i = 0; i < A.size(); i++) {
        int ind = A[i].find('-');
        if (ind + 1 < A[i].size() && isalpha(A[i][ind + 1])) {
            letter.push_back({A[i].substr(0, ind), A[i].substr(ind + 1)});
        } else {
            digit.push_back(A[i]);
        }
    }

    sort(letter.begin(), letter.end(), mycompare);

    for (auto &val : letter) {
        res_vec.push_back(val.first + "-" + val.second);
    }
    for (auto &val : digit) {
        res_vec.push_back(val);
    }

    return res_vec;
}
```

#### Second Solution:

```cpp
bool isDigit(char c)
{
    return c >= '0' && c <= '9';
}

bool logComp(string a, string b)
{
    // Split by space, not dash (correct delimiter)
    int stA = a.find(' ');
    int stB = b.find(' ');
    
    // Extract identifier and content
    string logHeaderA(a.begin(), a.begin() + stA);
    string logHeaderB(b.begin(), b.begin() + stB);

    string logA(a.begin() + stA + 1, a.end());
    string logB(b.begin() + stB + 1, b.end());

    // Check if each log is digit-log or letter-log
    bool isDigitA = isDigit(logA[0]);
    bool isDigitB = isDigit(logB[0]);

    // Letter-log comes before digit-log
    if (isDigitA && !isDigitB)
        return false;

    if (!isDigitA && isDigitB)
	    return true;

    // Both are letter-logs: compare content, then identifier
    if (!isDigitA && !isDigitB) {
        if (logA == logB)
            return logHeaderA < logHeaderB;
        return logA < logB;
    }

    // Both are digit-logs: maintain original order (stable_sort handles it)
    return false;
}

vector<string> Solution::reorderLogs(vector<string> &A) {
    stable_sort(A.begin(), A.end(), logComp); 
    return A;
}
```
#### Complexity

- Time Complexity: O(nmLogn)
- Space Complexity: O(nm)