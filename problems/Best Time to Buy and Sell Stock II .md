# Best Time to Buy and Sell Stock II

> [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

## Tags

> [Array](../tags/Array.md)

> [Greedy](../tags/Greedy.md)

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
        int minValue = prices[0];
        int mProfit = 0;
        for (int i=1; i<pricesSize; i++){
            if (prices[i]<minValue){
                minValue = prices[i];
            }else if (prices[i]> minValue){
                int profit = prices[i]-minValue;
                if ( i== pricesSize-1 || prices[i+1]<=prices[i]){
                    mProfit += profit;
                    minValue = prices[i];
                }
            }
        }
        return mProfit;
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
        int minValue = prices[0];
        int mProfit = 0;
        for (int i=1; i<pricesSize; i++){
            if (prices[i]<minValue){
                minValue = prices[i];
            }else if (prices[i]> minValue){
                int profit = prices[i]-minValue;
                if ( i== pricesSize-1 || prices[i+1]<=prices[i]){
                    mProfit += profit;
                    minValue = prices[i];
                }
            }
        }
        return mProfit;
    }
}
```

### c

```c
int maxProfit(int* prices, int pricesSize) {
    if (pricesSize < 2){
        return 0;
    }
    int minValue = prices[0];
    int mProfit = 0;
    for (int i=1; i<pricesSize; i++){
        if (prices[i]<minValue){
            minValue = prices[i];
        }else if (prices[i]> minValue){
            int profit = prices[i]-minValue;
            if ( i== pricesSize-1 || prices[i+1]<=prices[i]){
                mProfit += profit;
                minValue = prices[i];
            }
        }
    }
    return mProfit;
}
```