# Rotate Array

> [https://leetcode.com/problems/rotate-array/](https://leetcode.com/problems/rotate-array/)

## Tags

> [Array](../tags/Array.md)

## Solutions

### cpp

```cpp
class Solution {
private:
    int calGcd(int a, int b){
        int mod = a % b;
        while (mod != 0){
            a = b;
            b = mod;
            mod  = a % b;
        }
        return b;
    }
public:
    void rotate(vector<int>& nums, int k) {
        int numsSize = nums.size();
        if (numsSize == 0){
            return;
        }
        int mod =  k % numsSize;
        int p = (numsSize - mod) % numsSize;
        if (p == 0){
            return;
        }
        int gcd = calGcd(numsSize, p);
        for (int i=0; i<gcd; i++){
            int value = nums[i];
            int last = i;
            int next = (last + p) % numsSize;
            while (next != i){
                 nums[last] = nums[next];
                 last = next;
                 next = (last + p) % numsSize;
            }
            nums[last] = value;
        }
    }
};
```

### c

```c
void rotate(int* nums, int numsSize, int k) {
    if (numsSize == 0){
        return;
    }
    int mod =  k % numsSize;
    int p = (numsSize - mod) % numsSize;
    if (p == 0){
        return;
    }
    
    int a = numsSize;
    int b = p;
    int md = a % b;
    while (md != 0){
        a = b;
        b = md;
        md  = a % b;
    }

    for (int i=0; i<b; i++){
        int value = nums[i];
        int last = i;
        int next = (last + p) % numsSize;
        while (next != i){
             nums[last] = nums[next];
             last = next;
             next = (last + p) % numsSize;
        }
        nums[last] = value;
    }
}
```

### java

```java
public class Solution {
    
    int gcd(int a, int b){
        int mod = a % b;
        while (mod != 0){
            a = b;
            b = mod;
            mod  = a % b;
        }
        return b;
    }
    public void rotate(int[] nums, int k) {
        int numsSize = nums.length;
        if (numsSize == 0){
            return;
        }
        int mod =  k % numsSize;
        int p = (numsSize - mod) % numsSize;
        if (p == 0){
            return;
        }
        int gcd = gcd(numsSize, p);
        for (int i=0; i<gcd; i++){
            int value = nums[i];
            int last = i;
            int next = (last + p) % numsSize;
            while (next != i){
                 nums[last] = nums[next];
                 last = next;
                 next = (last + p) % numsSize;
            }
            nums[last] = value;
        }
    }
}
```