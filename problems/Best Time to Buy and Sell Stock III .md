# Best Time to Buy and Sell Stock III

> [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)

## Tags

> [Array](../tags/Array.md)

> [Dynamic Programming](../tags/Dynamic Programming.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int pricesSize = prices.size();
        if (pricesSize < 2){
            return 0;
        }
        int f[2][5];
        f[0][0] = prices[0];
        f[0][1] = 0;
        f[0][2] = -214748364;
        f[0][3] = 214748364;
        f[0][4] = 0;
        
        for (int i=1; i<pricesSize; i++){
            int n = i & 1;
            int l = 1 - n;
            int p = prices[i];
            f[n][0] = min(f[l][0], p);
            f[n][1] = max(f[l][1], p - f[l][0]);
            
            int v1 = f[l][1] - p;
            int v2 = f[l][2];
            if (v1 > v2){
                f[n][2] = v1;
                f[n][3] = p;
            } else{
                f[n][2] = v2;
                f[n][3] = f[l][3];
            }
            if (p < f[l][3]){
                int v3 = f[l][2] + f[l][3] - p;
                if (v3 > f[n][2]){
                    f[n][2] = v3;
                    f[n][3] = p;
                }
            }
            f[n][4] = max(f[l][4], max(f[l][2]+p, f[n][1]));
        }
        int index = 1 - (pricesSize & 1);
        return f[index][4];
    }
};
```

### java

```java
public class Solution {
    public int maxProfit(int[] prices) {
        int pricesSize = prices.length;
        if (pricesSize < 2){
            return 0;
        }
        int[][]f = new int[2][5];
        f[0][0] = prices[0];
        f[0][1] = 0;
        f[0][2] = -214748364;
        f[0][3] = 214748364;
        f[0][4] = 0;
        
        for (int i=1; i<pricesSize; i++){
            int n = i & 1;
            int l = 1 - n;
            int p = prices[i];
            f[n][0] = Math.min(f[l][0], p);
            f[n][1] = Math.max(f[l][1], p - f[l][0]);
            
            int v1 = f[l][1] - p;
            int v2 = f[l][2];
            if (v1 > v2){
                f[n][2] = v1;
                f[n][3] = p;
            } else{
                f[n][2] = v2;
                f[n][3] = f[l][3];
            }
            if (p < f[l][3]){
                int v3 = f[l][2] + f[l][3] - p;
                if (v3 > f[n][2]){
                    f[n][2] = v3;
                    f[n][3] = p;
                }
            }
            f[n][4] = Math.max(f[l][4], Math.max(f[l][2]+p, f[n][1]));
        }
        int index = 1 - (pricesSize & 1);
        return f[index][4];
    }
}
```

### c

```c
int min(int a, int b){
    return a < b ? a : b;
}

int max(int a, int b){
    return a > b ? a : b;
}

int maxProfit(int* prices, int pricesSize) {
    if (pricesSize < 2){
        return 0;
    }
    int f[2][5];
    f[0][0] = prices[0];
    f[0][1] = 0;
    f[0][2] = -214748364;
    f[0][3] = 214748364;
    f[0][4] = 0;
    
    for (int i=1; i<pricesSize; i++){
        int n = i & 1;
        int l = 1 - n;
        int p = prices[i];
        f[n][0] = min(f[l][0], p);
        f[n][1] = max(f[l][1], p - f[l][0]);
        
        int v1 = f[l][1] - p;
        int v2 = f[l][2];
        if (v1 > v2){
            f[n][2] = v1;
            f[n][3] = p;
        } else{
            f[n][2] = v2;
            f[n][3] = f[l][3];
        }
        if (p < f[l][3]){
            int v3 = f[l][2] + f[l][3] - p;
            if (v3 > f[n][2]){
                f[n][2] = v3;
                f[n][3] = p;
            }
        }
        f[n][4] = max(f[l][4], max(f[l][2]+p, f[n][1]));
    }
    int index = 1 - (pricesSize & 1);
    return f[index][4];
}
```