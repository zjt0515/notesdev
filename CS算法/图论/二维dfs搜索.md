### [695. 岛屿的最大面积](https://leetcode.cn/problems/max-area-of-island/)

```c++
class Solution {
public:
    int maxAreaOfIsland(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        
        int res = 0;
        function<int(int,int)> dfs = [&](int i,int j){
            if(i < 0 || j < 0 || i >= n || j >= m) return 0;
            if(grid[i][j] == 2 || grid[i][j] ==0) return 0;
            grid[i][j] = 2;
            return 1+dfs(i-1,j)+dfs(i,j-1)+dfs(i,j+1)+dfs(i+1,j);
            
        };
        for(int i = 0; i < n; i++){
            for(int j = 0; j < m; j++){
                if(grid[i][j] == 1) {
                    res = max(dfs(i,j),res);
                }
            }
        }
        return res;
    }
};
```

