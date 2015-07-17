# Plus One

> [https://leetcode.com/problems/plus-one/](https://leetcode.com/problems/plus-one/)

## Tags

> [Array](../tags/Array.md)

> [Math](../tags/Math.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int digitsSize = digits.size();
        for (int i= digitsSize-1; i>=0; i--){
            if (digits[i]==9){
                digits[i]=0;
            }else{
                digits[i]++;
                return digits;
            }
        }
        vector<int> re(digitsSize+1, 0);
        re[0] = 1;
        return re;
    }
};
```

### c

```c
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize) {
    int* re = malloc(sizeof(int) * (digitsSize+1));
    for (int i= digitsSize-1; i>=0; i--){
        if (digits[i]==9){
            re[i] = 0;
        }else{
            re[i] = digits[i] + 1;
            *returnSize = digitsSize;
            memcpy(re, digits, sizeof(int) * i);
            return re;
        }
    }
    re[0] = 1;
    re[digitsSize] = 0;
    *returnSize = digitsSize+1;
    return re;
}
```

### java

```java
public class Solution {
    public int[] plusOne(int[] digits) {
        for (int i= digits.length-1; i>=0; i--){
            if (digits[i]==9){
                digits[i]=0;
            }else{
                digits[i]++;
                return digits;
            }
        }
        int[] re = new int[digits.length+1];
        re[0] = 1;
        return re;
    }
}
```