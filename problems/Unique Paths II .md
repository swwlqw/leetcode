# Unique Paths II

> [https://leetcode.com/problems/unique-paths-ii/](https://leetcode.com/problems/unique-paths-ii/)

## Tags

> [Array](../tags/Array.md)

> [Dynamic Programming](../tags/Dynamic Programming.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size();
        int n = obstacleGrid[0].size();
        if(obstacleGrid[0][0] == 1){
            return 0;
        }
        obstacleGrid[0][0] = 1;
        for (int i=1; i< m; i++){
            if (obstacleGrid[i-1][0]==1){
                obstacleGrid[i][0] = 1 - obstacleGrid[i][0];
            } else{
                obstacleGrid[i][0] = 0;
            }
        }
        for (int i=1; i< n; i++){
            if (obstacleGrid[0][i-1]==1){
                obstacleGrid[0][i] = 1 - obstacleGrid[0][i];
            } else{
                obstacleGrid[0][i] = 0;
            }
        }
        for (int i=1; i<m; i++){
            for (int j=1; j<n; j++){
                if (obstacleGrid[i][j]==1){
                    obstacleGrid[i][j] = 0;
                }else{
                    obstacleGrid[i][j] = obstacleGrid[i-1][j] + obstacleGrid[i][j-1];
                }
            }
        }
        return obstacleGrid[m-1][n-1];
    }
};
```

### c

```c
int uniquePathsWithObstacles(int** obstacleGrid, int obstacleGridRowSize, int obstacleGridColSize) {
    int m = obstacleGridRowSize;
    int n = obstacleGridColSize;
    if(obstacleGrid[0][0] == 1){
        return 0;
    }
    obstacleGrid[0][0] = 1;
    for (int i=1; i< m; i++){
        if (obstacleGrid[i-1][0]==1){
            obstacleGrid[i][0] = 1 - obstacleGrid[i][0];
        } else{
            obstacleGrid[i][0] = 0;
        }
    }
    for (int i=1; i< n; i++){
        if (obstacleGrid[0][i-1]==1){
            obstacleGrid[0][i] = 1 - obstacleGrid[0][i];
        } else{
            obstacleGrid[0][i] = 0;
        }
    }
    for (int i=1; i<m; i++){
        for (int j=1; j<n; j++){
            if (obstacleGrid[i][j]==1){
                obstacleGrid[i][j] = 0;
            }else{
                obstacleGrid[i][j] = obstacleGrid[i-1][j] + obstacleGrid[i][j-1];
            }
        }
    }
    return obstacleGrid[m-1][n-1];
}
```

### java

```java
public class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length;
        int n = obstacleGrid[0].length;
        if(obstacleGrid[0][0] == 1){
            return 0;
        }
        obstacleGrid[0][0] = 1;
        for (int i=1; i< m; i++){
            if (obstacleGrid[i-1][0]==1){
                obstacleGrid[i][0] = 1 - obstacleGrid[i][0];
            } else{
                obstacleGrid[i][0] = 0;
            }
        }
        for (int i=1; i< n; i++){
            if (obstacleGrid[0][i-1]==1){
                obstacleGrid[0][i] = 1 - obstacleGrid[0][i];
            } else{
                obstacleGrid[0][i] = 0;
            }
        }
        for (int i=1; i<m; i++){
            for (int j=1; j<n; j++){
                if (obstacleGrid[i][j]==1){
                    obstacleGrid[i][j] = 0;
                }else{
                    obstacleGrid[i][j] = obstacleGrid[i-1][j] + obstacleGrid[i][j-1];
                }
            }
        }
        return obstacleGrid[m-1][n-1];
    }
}
```