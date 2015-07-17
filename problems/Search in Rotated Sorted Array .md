# Search in Rotated Sorted Array

> [https://leetcode.com/problems/search-in-rotated-sorted-array/](https://leetcode.com/problems/search-in-rotated-sorted-array/)

## Tags

> [Array](../tags/Array.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
class Solution {
private:
    int search(vector<int>& nums, int target, int start, int end){
        if (start == end){
            return -1;
        }
        if (nums[start]==target){
            return start;
        }
        if (start==end-1){
            return -1;
        }else{
            int mid =(start+ end)/2;
            if (nums[mid]==target){
                return mid;
            }
            if (nums[start]<nums[mid]){
                if (target>nums[start] && target<nums[mid]){
                    return search(nums, target, start+1, mid);
                }else{
                    return search(nums, target, mid+1, end);
                }
            }else{
                if (target>nums[mid] && target<nums[start]){
                    return search(nums, target, mid+1, end);
                }else{
                    return search(nums, target, start+1, mid);
                }
            }
        }
    }
public:
    int search(vector<int>& nums, int target) {
        int numsSize = nums.size();
        return search(nums, target, 0, numsSize);
    }
};
```

### c

```c
int search(int* nums, int numsSize, int target) {
    int start = 0;
    int end = numsSize;
    while (1){
        if (start == end){
            return -1;
        }
        if (nums[start]==target){
            return start;
        }
        if (start==end-1){
            return -1;
        }else{
            int mid =(start+ end)/2;
            if (nums[mid]==target){
                return mid;
            }
            if (nums[start]<nums[mid]){
                if (target>nums[start] && target<nums[mid]){
                    start = start + 1;
                    end = mid;
                }else{
                    start = mid + 1;
                }
            }else{
                if (target>nums[mid] && target<nums[start]){
                    start = mid + 1;
                }else{
                    start = start + 1;
                    end = mid;
                }
            }
        }
    }
}
```

### java

```java
public class Solution {
    private int search(int[]nums, int target, int start, int end){
        if (start == end){
            return -1;
        }
        if (nums[start]==target){
            return start;
        }
        if (start==end-1){
            return -1;
        }else{
            int mid =(start+ end)/2;
            if (nums[mid]==target){
                return mid;
            }
            if (nums[start]<nums[mid]){
                if (target>nums[start] && target<nums[mid]){
                    return search(nums, target, start+1, mid);
                }else{
                    return search(nums, target, mid+1, end);
                }
            }else{
                if (target>nums[mid] && target<nums[start]){
                    return search(nums, target, mid+1, end);
                }else{
                    return search(nums, target, start+1, mid);
                }
            }
        }
    }
    public int search(int[] nums, int target) {
        int numsSize = nums.length;
        return search(nums, target, 0, numsSize);
    }
}
```