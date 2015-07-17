# Search in Rotated Sorted Array II

> [https://leetcode.com/problems/search-in-rotated-sorted-array-ii/](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

## Tags

> [Array](../tags/Array.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
class Solution {
private:
    bool search(vector<int>& nums, int target, int start, int end){
        if (start == end){
            return false;
        }
        if (nums[start]==target){
            return true;
        }
        if (start==end-1){
            return false;
        }else{
            int mid =(start+ end)/2;
            if (nums[mid]==target){
                return true;
            }
            if (nums[start]<nums[mid]){
                if (target>nums[start] && target<nums[mid]){
                    return search(nums, target, start+1, mid);
                }else{
                    return search(nums, target, mid+1, end);
                }
            }else if (nums[start]>nums[mid]){
                if (target>nums[mid] && target<nums[start]){
                    return search(nums, target, mid+1, end);
                }else{
                    return search(nums, target, start+1, mid);
                }
            }else{
                return search(nums, target, mid+1, end) || search(nums, target, start+1, mid);
            }
        }
    }
public:
    bool search(vector<int>& nums, int target) {
        int numsSize = nums.size();
        return search(nums, target, 0, numsSize);
    }
};
```

### java

```java
public class Solution {
    public boolean search(int[] nums, int target) {
        for (int num: nums){
            if(num == target){
                return true;
            }
        }
        return false;
    }
}
```

### c

```c
bool search2(int* nums, int target, int start, int end){
    if (start == end){
        return false;
    }
    if (nums[start]==target){
        return true;
    }
    if (start==end-1){
        return false;
    }else{
        int mid =(start+ end)/2;
        if (nums[mid]==target){
            return true;
        }
        if (nums[start]<nums[mid]){
            if (target>nums[start] && target<nums[mid]){
                return search2(nums, target, start+1, mid);
            }else{
                return search2(nums, target, mid+1, end);
            }
        }else if (nums[start]>nums[mid]){
            if (target>nums[mid] && target<nums[start]){
                return search2(nums, target, mid+1, end);
            }else{
                return search2(nums, target, start+1, mid);
            }
        }else{
            return search2(nums, target, mid+1, end) || search2(nums, target, start+1, mid);
        }
    }
}

bool search(int* nums, int numsSize, int target) {
    return search2(nums, target, 0, numsSize);
}
```