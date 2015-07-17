# Unique Paths

> [https://leetcode.com/problems/unique-paths/](https://leetcode.com/problems/unique-paths/)

## Tags

> [Array](../tags/Array.md)

> [Dynamic Programming](../tags/Dynamic Programming.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int uniquePaths(int m, int n) {
        int small, large;
        if (m < n){
            small = m - 1;
            large = n - 1;
        }else {
            small = n - 1;
            large = m - 1;
        }
        long d = 1;
        long q = 1;
        for (int i=1; i<=small; i++){
            d *= (large + i);
            q *= i;
        }
        int re = (int) (d / q);
        return re;
    }
};
```

### c

```c
int uniquePaths(int m, int n) {
    int small, large;
    if (m < n){
        small = m - 1;
        large = n - 1;
    }else {
        small = n - 1;
        large = m - 1;
    }
    long d = 1;
    long q = 1;
    for (int i=1; i<=small; i++){
        d *= (large + i);
        q *= i;
    }
    int re = (int) (d / q);
    return re;
}
```

### java

```java
public class Solution {
    public int uniquePaths(int m, int n) {
        int small, large;
        if (m < n){
            small = m - 1;
            large = n - 1;
        }else {
            small = n - 1;
            large = m - 1;
        }
        long d = 1;
        long q = 1;
        for (int i=1; i<=small; i++){
            d *= (large + i);
            q *= i;
        }
        int re = (int) (d / q);
        return re;
    }
}
```