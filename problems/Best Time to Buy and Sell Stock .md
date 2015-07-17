# Best Time to Buy and Sell Stock

> [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

## Tags

> [Array](../tags/Array.md)

> [Dynamic Programming](../tags/Dynamic Programming.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (prices.size()<2){
            return 0;
        }
        int minValue = prices[0];
        int mProfit = 0;
        for (int i=1; i<prices.size(); i++){
            if (prices[i]<minValue){
                minValue= prices[i];
            }else if (prices[i]>minValue){
                int profit = prices[i]-minValue;
                if (profit > mProfit){
                    mProfit = profit;
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
        if (prices.length<2){
            return 0;
        }
        int minValue = prices[0];
        int mProfit = 0;
        for (int i=1; i<prices.length; i++){
            if (prices[i]<minValue){
                minValue= prices[i];
            }else if (prices[i]>minValue){
                int profit = prices[i]-minValue;
                mProfit = Math.max(mProfit, profit);
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
        }else{
            int profit = prices[i]-minValue;
            if (profit>mProfit){
                mProfit = profit;
            }
        }
    }
    return mProfit;
}
```