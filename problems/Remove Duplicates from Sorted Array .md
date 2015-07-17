# Remove Duplicates from Sorted Array

> [https://leetcode.com/problems/remove-duplicates-from-sorted-array/](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## Tags

> [Array](../tags/Array.md)

> [Two Pointers](../tags/Two Pointers.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size() ==0){
            return 0;
        }
        int last = nums[0];
        int count = 1;
        int index = 1;
        for (int i=1; i<nums.size(); i++){
            if (nums[i]!= last){
                last = nums[i];
                count++;
                nums[index++]=last;
            }
        }
        return count;
    }
};
```

### c

```c
int removeDuplicates(int* nums, int numsSize) {
    if (numsSize==0){
        return 0;
    }
    int last = nums[0];
    int index = 1;
    for (int i=1; i<numsSize; i++){
        if (nums[i]!= last){
            last = nums[i];
            nums[index++]=last;
        }
    }
    return index;
}
```

### java

```java
public class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length ==0){
            return 0;
        }
        int last = nums[0];
        int count = 1;
        int index = 1;
        for (int i=1;i<nums.length;i++){
            if (nums[i]!= last){
                last = nums[i];
                count++;
                nums[index++]=last;
            }
        }
        return count;
    }
}
```