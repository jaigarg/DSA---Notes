#dsa #arrays #greedy 
### [Maximum Area of Triangle!](https://www.interviewbit.com/problems/maximum-area-of-triangle/)
? 
#### Explanation

Calculate the left most, right most points of each color. Similarly calculate the top most and bottom most point in each column for each color. Now, visit every column and take top of one color, bottom of second color and left/right most points of third color to calculate maximum area. This is a very specific format/approach based question with focus on how to write the solution in a clean and effective manner.
#### Solution

```cpp
int Solution::solve(vector<string> &A) {
    int n = A.size();
    int m = A[0].size();
    
    vector<int> left(3, INT_MAX);
    vector<int> right(3, INT_MIN);
    vector<vector<int>> top(m, vector<int>(3, INT_MAX));
    vector<vector<int>> bottom(m, vector<int>(3, INT_MIN));
    
    unordered_map<char, int> umap;
    umap['r'] = 0;
    umap['g'] = 1;
    umap['b'] = 2;
    
    // Preprocessing to find extreme coordinates for each color
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            int val = umap[A[i][j]];
            left[val] = min(left[val], j);
            right[val] = max(right[val], j);
            top[j][val] = min(top[j][val], i);
            bottom[j][val] = max(bottom[j][val], i);
        }        
    }
    
    double res = 0;
    
    // Try all combinations of triangle vertices with distinct colors
    for (int i = 0; i < m; i++) {
        for (int x = 0; x < 3; x++) {
            for (int y = 0; y < 3; y++) {
                int z = 3 - x - y;
                
                if (x != y) {
                    if (top[i][x] != INT_MAX && bottom[i][y] != INT_MIN && left[z] != INT_MAX) {
                        double possible_area = 0.5 * (abs(top[i][x] - bottom[i][y]) + 1) * (abs(left[z] - i) + 1);
                        res = max(res, possible_area);
                    }
                    
                    if (top[i][x] != INT_MAX && bottom[i][y] != INT_MIN && right[z] != INT_MIN) {
                        double possible_area = 0.5 * (abs(top[i][x] - bottom[i][y]) + 1) * (abs(right[z] - i) + 1);
                        res = max(res, possible_area);
                    }
                }
            }
        }
    }
    
    return ceil(res);
}
```

#### Complexity

- Time Complexity: O(n x m)
- Space Complexity: O(m)