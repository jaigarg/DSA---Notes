#dsa #arrays #sort #intervals #2Pointer #greedy 
### [Hotel Booking Possible](https://www.interviewbit.com/problems/hotel-bookings-possible/)
? 
#### Explanation

This question involves sorting both arrival and departure arrays and then traversing over them to identify the maximum number of rooms required for each iteration. At any point of time, if the number of rooms required exceed number of total rooms, return false. Otherwise, we can return true at the end.
#### Solution

```cpp
bool Solution::hotel(vector<int> &arrive, vector<int> &depart, int K) {
    vector<int> sortArrive(arrive.begin(), arrive.end());
    vector<int> sortDepart(depart.begin(), depart.end());
    
    sort(sortArrive.begin(), sortArrive.end());
    sort(sortDepart.begin(), sortDepart.end());
    
    int i = 0, j = 0;
    int n = arrive.size();
    int curRoom = 0;
    while(i < n)
    {
        if(sortArrive[i] <= sortDepart[j])
        {
            curRoom++;
            i++;
        }
        else
        {
            curRoom--;
            j++;
        }
        if(curRoom > K)
        {
            return false;
        }
    }
    return true;
}
```

#### Complexity

- Time Complexity: O(nLogn)
- Space Complexity: O(n)