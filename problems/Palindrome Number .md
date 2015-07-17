# Palindrome Number

> [https://leetcode.com/problems/palindrome-number/](https://leetcode.com/problems/palindrome-number/)

## Tags

> [Math](../tags/Math.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if (x<0)
            return false;
        if (x<10)
            return true;
        int y = 0;
        int t = x;
        while (t>0){
            int mod = t % 10;
            t /= 10;
            y= y*10 + mod;
        }
        return x==y;
    }
};
```

### java

```java
public class Solution {
    public boolean isPalindrome(int x) {
        if (x<0)
            return false;
        if (x<10)
            return true;
        int y = 0;
        int t = x;
        while (t>0){
            int mod = t % 10;
            t /= 10;
            y= y*10 + mod;
        }
        return x==y;
    }
}
```

### c

```c
bool isPalindrome(int x) {
    if (x<0)
        return false;
    if (x<10)
        return true;
    int y = 0;
    int t = x;
    while (t){
        int mod = t % 10;
        t /= 10;
        y= y*10 + mod;
    }
    return x==y;
}
```