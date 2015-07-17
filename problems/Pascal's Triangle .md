# Pascal's Triangle

> [https://leetcode.com/problems/pascals-triangle/](https://leetcode.com/problems/pascals-triangle/)

## Tags

> [Array](../tags/Array.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> re;
        for (int i=0; i<numRows; i++){
            int n = i+1;
            vector<int> list(n);
            list[0] = 1;
            list[i] = 1;
            for (int j=1; j<i; j++){
                list[j] = re[i-1][j-1] + re[i-1][j];
            }
            re.push_back(list);
        }
        return re;
    }
};
```

### java

```java
public class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> re= new ArrayList<List<Integer>>();
        for (int i=0; i<numRows; i++){
            int n = i+1;
            List<Integer> list = new ArrayList<Integer>(n);
            list.add(1);
            for (int j=1; j<i; j++){
                List<Integer> last = re.get(i-1);
                list.add(last.get(j-1)+last.get(j));
            }
            if (n>1){
                list.add(1);
            }
            re.add(list);
        }
        return re;
    }
}
```

### c

```c
/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *columnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** generate(int numRows, int** columnSizes, int* returnSize){
    *returnSize = numRows;
    int** re = malloc(sizeof(int*) * numRows);
    *columnSizes = malloc(sizeof(int) * numRows);
    for (int i=0; i<numRows; i++){
        int n = i+1;
        (*columnSizes)[i] = n;
        re[i] = malloc(sizeof(int)*n);
        re[i][0] = 1;
        re[i][i] = 1;
        for (int j=1; j<i; j++){
            re[i][j] = re[i-1][j-1] + re[i-1][j];
        }
    }
    return re;
}
```