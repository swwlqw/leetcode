# Find Peak Element

> [https://leetcode.com/problems/find-peak-element/](https://leetcode.com/problems/find-peak-element/)

## Tags

> [Array](../tags/Array.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int findPeakElement(vector<int>& nums, int left, int right){
        int mid = (left + right) / 2;
        int a = nums[mid-1];
        int b = nums[mid];
        int c = nums[mid+1];
        if (a < b ){
            if (b > c) {
                return mid;
            }else{
                return findPeakElement(nums, mid, right);
            }
        } else{
            return findPeakElement(nums, left, mid);
        }
    }

    int findPeakElement(vector<int>& nums) {
        int numsSize = nums.size();
        if (numsSize == 1){
            return 0;
        }
        if (nums[1]<nums[0]){
            return 0;
        }
        if (nums[numsSize-2]< nums[numsSize-1]){
            return numsSize - 1;
        }
        return findPeakElement(nums, 0, numsSize -1);
    }
};
```

### c

```c

int findPeakElement2(int* nums, int left, int right){
    int mid = (left + right) / 2;
    int a = nums[mid-1];
    int b = nums[mid];
    int c = nums[mid+1];
    if (a < b ){
        if (b > c) {
            return mid;
        }else{
            return findPeakElement2(nums, mid, right);
        }
    } else{
        return findPeakElement2(nums, left, mid);
    }
}
int findPeakElement(int* nums, int numsSize) {
    if (numsSize == 1){
        return 0;
    }
    if (nums[1]<nums[0]){
        return 0;
    }
    if (nums[numsSize-2]< nums[numsSize-1]){
        return numsSize - 1;
    }
    return findPeakElement2(nums, 0, numsSize -1);
}
```

### java

```java
public class Solution {
    int findPeakElement(int[] nums, int left, int right){
        int mid = (left + right) / 2;
        int a = nums[mid-1];
        int b = nums[mid];
        int c = nums[mid+1];
        if (a < b ){
            if (b > c) {
                return mid;
            }else{
                return findPeakElement(nums, mid, right);
            }
        } else{
            return findPeakElement(nums, left, mid);
        }
    }
    public int findPeakElement(int[] nums) {
        int numsSize = nums.length;
        if (numsSize == 1){
            return 0;
        }
        if (nums[1]<nums[0]){
            return 0;
        }
        if (nums[numsSize-2]< nums[numsSize-1]){
            return numsSize - 1;
        }
        return findPeakElement(nums, 0, numsSize -1);
    }
}
```