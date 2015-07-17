# Sort Colors

> [https://leetcode.com/problems/sort-colors/](https://leetcode.com/problems/sort-colors/)

## Tags

> [Array](../tags/Array.md)

> [Two Pointers](../tags/Two Pointers.md)

> [Sort](../tags/Sort.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int numsSize = nums.size();
        if (numsSize == 0){
            return;
        }
        int p = 0;
        int q = numsSize - 1;
        while(p<numsSize && nums[p]==0){
            p++;
        }
        while(q>=0 && nums[q]==2){
            q--;
        }
        int r = p;
        while (r<numsSize && nums[r]==1){
            r++;
        }
        while (r<=q){
            if (nums[r]==0){
                nums[r]=nums[p];
                nums[p]=0;
            }else{
                nums[r]=nums[q];
                nums[q]=2;
            }
            while(p<numsSize && nums[p]==0){
                p++;
            }
            while(q>=0 && nums[q]==2){
                q--;
            }
            if (r < p){
                r = p;
            }
            while (r<numsSize && nums[r]==1){
                r++;
            }
        }
    }
};
```

### c

```c
void sortColors(int* nums, int numsSize) {
    if (numsSize == 0){
        return;
    }
    int p = 0;
    int q = numsSize - 1;
    while(p<numsSize && nums[p]==0){
        p++;
    }
    while(q>=0 && nums[q]==2){
        q--;
    }
    int r = p;
    while (r<numsSize && nums[r]==1){
        r++;
    }
    while (r<=q){
        if (nums[r]==0){
            nums[r]=nums[p];
            nums[p]=0;
        }else{
            nums[r]=nums[q];
            nums[q]=2;
        }
        while(p<numsSize && nums[p]==0){
            p++;
        }
        while(q>=0 && nums[q]==2){
            q--;
        }
        if (r < p){
            r = p;
        }
        while (r<numsSize && nums[r]==1){
            r++;
        }
    }
}
```

### java

```java
public class Solution {
    public void sortColors(int[] nums) {
        int numsSize = nums.length;
        if (numsSize == 0){
            return;
        }
        int p = 0;
        int q = numsSize - 1;
        while(p<numsSize && nums[p]==0){
            p++;
        }
        while(q>=0 && nums[q]==2){
            q--;
        }
        int r = p;
        while (r<numsSize && nums[r]==1){
            r++;
        }
        while (r<=q){
            if (nums[r]==0){
                nums[r]=nums[p];
                nums[p]=0;
            }else{
                nums[r]=nums[q];
                nums[q]=2;
            }
            while(p<numsSize && nums[p]==0){
                p++;
            }
            while(q>=0 && nums[q]==2){
                q--;
            }
            if (r < p){
                r = p;
            }
            while (r<numsSize && nums[r]==1){
                r++;
            }
        }
    }
}
```