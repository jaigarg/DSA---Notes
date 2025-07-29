#dsa #arrays #maths
### [Repeat and Missing Number](https://www.interviewbit.com/problems/repeat-and-missing-number-array/)
? 
#### Explanation

This is a pure mathematics based question, where we need to create a system of linear equation with rank 2, where two variables represent the repeated and the missing number. We just need to solve the equations to get the required numbers. The major part of the problem revolves around how to form the system of linear equations. For that we use below properties:
1. `Sum of first N natural numbers - Sum of given array = Repeated_Number - Missing_Number
2. `Sum of squares of first N natural numbers - Sum of squares of given array = Repeated_Number<sup>2</sup> - Missing_Number<sup>2</sup>`

This implies we have:
1. $a - b = K1$
2. $a$<sup>2</sup> - $b$<sup>2</sup> $= K2$

Solve these and we get a and b as answer.
#### Solution

```cpp
typedef long long ll;

vector<int> Solution::repeatedNumber(const vector<int> &A) {
    ll sum = 0;   // Difference of actual sum and expected sum
    ll ssum = 0;  // Difference of actual square sum and expected square sum
    int n = A.size();

    for(int i = 0; i < n; i++) {
        sum += (ll)A[i];
        sum -= (ll)(i + 1);
        ssum += (ll)A[i] * (ll)A[i];
        ssum -= (ll)(i + 1) * (ll)(i + 1);
    }

    // Let x = repeated, y = missing
    // sum = x - y
    // ssum = x^2 - y^2 = (x - y)(x + y) = sum * (x + y)

    ll eq1 = ssum / sum;           // x + y
    int repeated = (int)((eq1 + sum) / 2);  // x = (x + y + x - y)/2
    int missing = (int)(eq1 - repeated);    // y = x + y - x

    return {repeated, missing};
}
```

#### Complexity

- Time Complexity: O(n)
- Space Complexity: O(1)