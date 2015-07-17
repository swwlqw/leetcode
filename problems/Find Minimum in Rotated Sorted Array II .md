# Find Minimum in Rotated Sorted Array II

> [https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)

## Tags

> [Array](../tags/Array.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int min = nums[0];
        int numsSize = nums.size();
        for (int i=1; i<numsSize; i++){
            if (min>nums[i]){
                min = nums[i];
            }
        }
        return min;
    }
};
```

### java

```java
public class Solution {
    public int findMin(int[] nums) {
        int min = nums[0];
        int numsSize = nums.length;
        for (int i=1; i<numsSize; i++){
            if (min>nums[i]){
                min = nums[i];
            }
        }
        return min;
    }
}
```

### c

```c
int findMin(int* nums, int numsSize) {
    int min = nums[0];
    for (int i=1; i<numsSize; i++){
        if (min>nums[i]){
            min = nums[i];
        }
    }
    return min;
}
```