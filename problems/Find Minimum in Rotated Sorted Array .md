# Find Minimum in Rotated Sorted Array

> [https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

## Tags

> [Array](../tags/Array.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int start = 0;
        int end = nums.size();
        while (true){
            if (start==end-1){
                return nums[start];
            }else{
                int mid =(start+ end)/2;
                if (nums[start]<nums[mid]){
                    if (nums[start]<=nums[end-1]){
                        return nums[start];
                    }else{
                        start = mid + 1;
                    }
                }else{
                    if (nums[mid]<=nums[mid-1]){
                        return nums[mid];
                    }else{
                        end = mid;
                    }
                }
            }
        }
    }
};
```

### java

```java
public class Solution {
    public int findMin(int[] nums) {
        int start = 0;
        int end = nums.length;
        while (true){
            if (start==end-1){
                return nums[start];
            }else{
                int mid =(start+ end)/2;
                if (nums[start]<nums[mid]){
                    if (nums[start]<=nums[end-1]){
                        return nums[start];
                    }else{
                        start = mid + 1;
                    }
                }else{
                    if (nums[mid]<=nums[mid-1]){
                        return nums[mid];
                    }else{
                        end = mid;
                    }
                }
            }
        }
    }
}
```

### c

```c
int findMin(int* nums, int numsSize) {
    int start = 0;
    int end = numsSize;
    while (1){
        if (start==end-1){
            return nums[start];
        }else{
            int mid =(start+ end)/2;
            if (nums[start]<nums[mid]){
                if (nums[start]<=nums[end-1]){
                    return nums[start];
                }else{
                    start = mid + 1;
                }
            }else{
                if (nums[mid]<=nums[mid-1]){
                    return nums[mid];
                }else{
                    end = mid;
                }
            }
        }
    }
}
```