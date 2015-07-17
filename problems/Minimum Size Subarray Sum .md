# Minimum Size Subarray Sum

> [https://leetcode.com/problems/minimum-size-subarray-sum/](https://leetcode.com/problems/minimum-size-subarray-sum/)

## Tags

> [Array](../tags/Array.md)

> [Two Pointers](../tags/Two Pointers.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        int numsSize = nums.size();
        int start = 0;
        int sum = 0;
        int min = numsSize + 1;
        for (int i=0; i<numsSize; i++){
            sum += nums[i];
            while (sum >= s){
                int len = i - start + 1;
                if (min > len){
                    min = len;
                }
                sum -= nums[start];
                start++;
            }
        }
        if (min== numsSize+1){
            return 0;
        }else{
            return min;
        }
    }
};
```

### java

```java
public class Solution {
    public int minSubArrayLen(int s, int[] nums) {
        int numsSize = nums.length;
        int start = 0;
        int sum = 0;
        int min = numsSize + 1;
        for (int i=0; i<numsSize; i++){
            sum += nums[i];
            while (sum >= s){
                int len = i - start + 1;
                if (min > len){
                    min = len;
                }
                sum -= nums[start];
                start++;
            }
        }
        if (min== numsSize+1){
            return 0;
        }else{
            return min;
        }
    }
}
```

### c

```c
int minSubArrayLen(int s, int* nums, int numsSize) {
    int start = 0;
    int sum = 0;
    int min = numsSize + 1;
    for (int i=0; i<numsSize; i++){
        sum += nums[i];
        while (sum >= s){
            int len = i - start + 1;
            if (min > len){
                min = len;
            }
            sum -= nums[start];
            start++;
        }
    }
    if (min== numsSize+1){
        return 0;
    }else{
        return min;
    }
}
```