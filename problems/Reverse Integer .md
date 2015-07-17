# Reverse Integer

> [https://leetcode.com/problems/reverse-integer/](https://leetcode.com/problems/reverse-integer/)

## Tags

> [Math](../tags/Math.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int reverse(int x) {
        if (x==-2147483648){
            return 0;
        }
        if (x<0){
            return -(reverse(-x));
        }else{
            int re = 0;
            while (x){
                int mod = x % 10;
                x /= 10;
                if (x==0){
                    if (re < 214748364 || (re==214748364 && mod<=7)){
                        re = re * 10 + mod;
                    }else{
                        return 0;
                    }
                }else{
                    re = re * 10 + mod;   
                }
            }
            return re;
        }
    }
};
```

### java

```java
public class Solution {
    public int reverse(int x) {
        if (x==-2147483648){
            return 0;
        }
        if (x<0){
            return -(reverse(-x));
        }else{
            int re = 0;
            while (x > 0){
                int mod = x % 10;
                x /= 10;
                if (x==0){
                    if (re < 214748364 || (re==214748364 && mod<=7)){
                        re = re * 10 + mod;
                    }else{
                        return 0;
                    }
                }else{
                    re = re * 10 + mod;   
                }
            }
            return re;
        }
    }
}
```

### c

```c
int reverse(int x) {
    if (x==-2147483648){
        return 0;
    }
    if (x<0){
        return -(reverse(-x));
    }else{
        int re = 0;
        while (x){
            int mod = x % 10;
            x /= 10;
            if (x==0){
                if (re < 214748364 || (re==214748364 && mod<=7)){
                    re = re * 10 + mod;
                }else{
                    return 0;
                }
            }else{
                re = re * 10 + mod;   
            }
        }
        return re;
    }
}
```