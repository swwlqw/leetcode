# Single Number

> [https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)

## Tags

> [Hash Table](../tags/Hash Table.md)

> [Bit Manipulation](../tags/Bit Manipulation.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int singleNumber(int A[], int n) {
        int re =  0;
        for (int i=0;i<n;i++){
            re ^= A[i];
        }
        return re;
    }
};
```

### java

```java
public class Solution {
    public int singleNumber(int[] nums) {
        int re = 0;
        for (int num : nums){
            re ^= num;
        }
        return re;
    }
}
```

### c

```c
int singleNumber(int* nums, int numsSize) {
    int re = 0;
    for (int i=0; i<numsSize; i++){
        re  ^= nums[i];
    }
    return re;
}
```