#dsa #arrays 
### [Balance Array](https://www.interviewbit.com/problems/balance-array/)
? 
#### Explanation

This can be solved by calculation total even and odd index element sums. Then, we iterate over each element again and check whether it is special or not by checking the following:

`new_even_sum = cur_even_sum + (total_odd_sum - cur_odd_sum)`
`new_odd_sum = cur_odd_sum + (total_even_sum - cur_even_sum)`

If at any element we find `new_even_sum == new_odd_sum`, we increment the count of special numbers.
#### Solution

```cpp
int Solution::solve(vector<int> &A) {
    int tot_even = 0, tot_odd = 0;

    // Compute total even/odd index sums
    for (int i = 0; i < A.size(); i++) {
        if (i % 2 == 0) tot_even += A[i];
        else tot_odd += A[i];
    }

    int cur_even = 0, cur_odd = 0, res = 0;

    for (int i = 0; i < A.size(); i++) {
        int rem_even, rem_odd;

        if (i % 2 == 0) {
            rem_even = cur_even + tot_odd - cur_odd;
            rem_odd  = cur_odd + tot_even - cur_even - A[i];
            cur_even += A[i];
        } else {
            rem_even = cur_even + tot_odd - cur_odd - A[i];
            rem_odd  = cur_odd + tot_even - cur_even;
            cur_odd += A[i];
        }

        if (rem_even == rem_odd) res++;
    }

    return res;
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)