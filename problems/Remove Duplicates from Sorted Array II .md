# Remove Duplicates from Sorted Array II

> [https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)

## Tags

> [Array](../tags/Array.md)

> [Two Pointers](../tags/Two Pointers.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int numsSize = nums.size();
        if (numsSize==0){
            return 0;
        }
        int last = nums[0];
        int count = 1;
        int index = 1;
        for (int i=1; i< numsSize; i++){
            if (nums[i]!= last){
                last = nums[i];
                nums[index++]=last;
                count = 1;
            } else if (count == 1){
                nums[index++]=last;
                count ++;
            }
        }
        return index;
    }
};
```

### java

```java
public class Solution {
    public int removeDuplicates(int[] nums) {
        int numsSize = nums.length;
        if (numsSize==0){
            return 0;
        }
        int last = nums[0];
        int count = 1;
        int index = 1;
        for (int i=1; i< numsSize; i++){
            if (nums[i]!= last){
                last = nums[i];
                nums[index++]=last;
                count = 1;
            } else if (count == 1){
                nums[index++]=last;
                count ++;
            }
        }
        return index;
    }
}
```

### c

```c
int removeDuplicates(int* nums, int numsSize) {
    if (numsSize==0){
        return 0;
    }
    int last = nums[0];
    int count = 1;
    int index = 1;
    for (int i=1; i< numsSize; i++){
        if (nums[i]!= last){
            last = nums[i];
            nums[index++]=last;
            count = 1;
        } else {
            if (count == 1){
                nums[index++]=last;
                count ++;
            }
        }
    }
    return index;
}
```