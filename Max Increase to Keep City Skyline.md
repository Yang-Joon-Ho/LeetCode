[문제](https://leetcode.com/problems/max-increase-to-keep-city-skyline/)
----------


<br>
<br>

### 1. 코드

```cpp
class Solution {
public:
    int maxIncreaseKeepingSkyline(vector<vector<int>>& grid) {
        
        vector <int> l_r;
        vector <int> t_b;
        
        for(auto r : grid) {
            l_r.push_back(*max_element(r.begin(), r.end()));
        }
        
        for(int j = 0; j < grid.size(); j++) {
            int max_ele = 0;
            for(int i = 0; i < grid.size(); i++) 
                max_ele = grid[i][j] > max_ele ? grid[i][j] : max_ele;
            
            t_b.push_back(max_ele);
        }
        
        int answer = 0;
        
        for(int i = 0; i < grid.size(); i++) {
            for(int j = 0; j < grid.size(); j++) {
               answer += min(t_b[j], l_r[i]) - grid[i][j]; 
            }
        }
        
        return answer;
    }
};
```

<br>

### 2. 코멘트

    leetcode 문제들 되게 좋은것 같다. 
