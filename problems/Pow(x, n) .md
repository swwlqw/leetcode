# Pow(x, n)

> [https://leetcode.com/problems/powx-n/](https://leetcode.com/problems/powx-n/)

## Tags

> [Math](../tags/Math.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    double myLongPow(double x, long long n){
        double re = 1.0;
        long long i = 1;
        double temp = x;
        do{
            if (n & i){
                re *= temp;
            }
            i = i<<1;
            temp *=temp;
        }while(i<=n);
        return re;
    }
    
    double myPow(double x, int n) {
        long long ln = n;
        if (ln<0){
            return 1/myLongPow(x, -ln); 
        }else{
            return myLongPow(x, ln);
        }
    }
};
```

### java

```java
public class Solution {
    private double myLongPow(double x, long n){
        double re = 1.0;
        long i = 1;
        double temp = x;
        do{
            if ((n & i)!=0){
                re *= temp;
            }
            i = i<<1;
            temp *=temp;
        }while(i<=n);
        return re;
    }
    
    public double myPow(double x, int n) {
        long ln = n;
        if (ln<0){
            return 1/myLongPow(x, -ln); 
        }else{
            return myLongPow(x, ln);
        }
    }
}
```

### c

```c
double myLongPow(double x, long long n){
    double re = 1.0;
    long long i = 1;
    double temp = x;
    do{
        if (n & i){
            re *= temp;
        }
        i = i<<1;
        temp *=temp;
    }while(i<=n);
    return re;
}

double myPow(double x, int n) {
    long long ln = n;
    if (ln<0){
        return 1/myLongPow(x, -ln); 
    }else{
        return myLongPow(x, ln);
    }
}
```