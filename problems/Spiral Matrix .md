# Spiral Matrix

> [https://leetcode.com/problems/spiral-matrix/](https://leetcode.com/problems/spiral-matrix/)

## Tags

> [Array](../tags/Array.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> re;
        int rows = matrix.size();
        if (rows==0)
            return re;
        int cols = matrix[0].size();
        if (cols ==0)
            return re;
        int size = rows * cols;
        
        int row = 0;
        int col = 0;
        int direction = 0;
        int drow[] = {0, 1, 0, -1};
        int dcol[] = {1, 0, -1, 0};
        
        for (int i=0; i<size; i++){
            re.push_back(matrix[row][col]);
            matrix[row][col] = 0;
            
            int nrow = row + drow[direction];
            int ncol = col + dcol[direction];
            if (nrow<0 || ncol<0 || nrow>= rows || ncol>=cols || matrix[nrow][ncol] ==0 ){
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
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* spiralOrder(int** matrix, int matrixRowSize, int matrixColSize) {
    int size = matrixRowSize * matrixColSize;
    int* re = malloc(sizeof(int)* size);
    if (size == 0)
        return re;
    
    int row = 0;
    int col = 0;
    int direction = 0;
    int drow[] = {0, 1, 0, -1};
    int dcol[] = {1, 0, -1, 0};
    
    for (int i=0; i<size; i++){
        re[i] = matrix[row][col];
        matrix[row][col] = 0;
        int nrow = row + drow[direction];
        int ncol = col + dcol[direction];
        if (nrow<0 || ncol<0 || nrow>= matrixRowSize || ncol>=matrixColSize || matrix[nrow][ncol] ==0 ){
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
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> re = new ArrayList<Integer>();
        int rows = matrix.length;
        if (rows == 0)
            return re;
        int cols = matrix[0].length;
        if (cols == 0)
            return re;
        int size = rows * cols;
        
        int row = 0;
        int col = 0;
        int direction = 0;
        int[] drow = new int[]{0, 1, 0, -1};
        int[] dcol = new int[]{1, 0, -1, 0};
        
        for (int i=0; i<size; i++){
            re.add(matrix[row][col]);
            matrix[row][col] = 0;
            
            int nrow = row + drow[direction];
            int ncol = col + dcol[direction];
            if (nrow<0 || ncol<0 || nrow>= rows || ncol>=cols || matrix[nrow][ncol] ==0 ){
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