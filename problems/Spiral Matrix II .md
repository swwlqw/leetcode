# Spiral Matrix II

> [https://leetcode.com/problems/spiral-matrix-ii/](https://leetcode.com/problems/spiral-matrix-ii/)

## Tags

> [Array](../tags/Array.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<int> data(n, 0);
        vector<vector<int>> re(n, data);
        int n2 = n * n;
        int drow[] = {0, 1, 0, -1};
        int dcol[] = {1, 0, -1, 0};
        int direction = 0;
        
        int row = 0;
        int col = 0;
        for (int i=1; i<=n2; i++){
            re[row][col] = i;
            int nrow = row + drow[direction];
            int ncol = col + dcol[direction];
            if (nrow<0 || ncol<0 || nrow>= n || ncol>=n || re[nrow][ncol] !=0 ){
                direction = (direction +1) % 4;
                row += drow[direction];
                col += dcol[direction];
            }else{
                row = nrow;
                col = ncol;
            }
        }
        return re;
    }
};
```

### c

```c
/**
 * Return an array of arrays.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int** generateMatrix(int n) {
    int** re = malloc(sizeof(int*) * n);
    for (int i=0; i<n; i++){
        re[i] = malloc(sizeof(int) * n);
        memset(re[i], 0, sizeof(int) * n);
    }
    
    int n2 = n * n;
    int drow[] = {0, 1, 0, -1};
    int dcol[] = {1, 0, -1, 0};
    int direction = 0;
    
    int row = 0;
    int col = 0;
    for (int i=1; i<=n2; i++){
        re[row][col] = i;
        int nrow = row + drow[direction];
        int ncol = col + dcol[direction];
        if (nrow<0 || ncol<0 || nrow>= n || ncol>=n || re[nrow][ncol] !=0 ){
            direction = (direction +1) % 4;
            row += drow[direction];
            col += dcol[direction];
        }else{
            row = nrow;
            col = ncol;
        }
    }
    return re;
}
```

### java

```java
public class Solution {
    public int[][] generateMatrix(int n) {
        int[][] re = new int[n][n];
        int n2 = n * n;
        
        int[] drow = new int[]{0, 1, 0, -1};
        int[] dcol = new int[]{1, 0, -1, 0};
        int direction = 0;
        
        int row = 0;
        int col = 0;
        for (int i=1; i<=n2; i++){
            re[row][col] = i;
            int nrow = row + drow[direction];
            int ncol = col + dcol[direction];
            if (nrow<0 || ncol<0 || nrow>= n || ncol>=n || re[nrow][ncol] !=0 ){
                direction = (direction +1) % 4;
                row += drow[direction];
                col += dcol[direction];
            }else{
                row = nrow;
                col = ncol;
            }
        }
        return re;
    }
}
```