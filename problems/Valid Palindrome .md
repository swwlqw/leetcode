# Valid Palindrome

> [https://leetcode.com/problems/valid-palindrome/](https://leetcode.com/problems/valid-palindrome/)

## Tags

> [Two Pointers](../tags/Two Pointers.md)

> [String](../tags/String.md)

## Solutions

### cpp

```cpp
class Solution {
public:

    int getCode(char ch){
        if (ch>='0' && ch<='9'){
            return ch;
        }
        if (ch>='A' && ch<='Z'){
            return ch +('a'-'A');
        }
        if (ch>='a' && ch<='z'){
            return ch;
        }
        return 0;
    }
    bool isPalindrome(string s) {
        int len = s.size();
        if (len<=1){
            return true;
        }
        int p = 0;
        int q = len -1;
        do{
            while (p<len && !getCode(s[p])){
                p++;
            }
            while (q>=0 && !getCode(s[q])){
                q--;
            }
            if (p<q && getCode(s[p])!= getCode(s[q])){
                return false;
            }
            p++;
            q--;
        }while (p<q);
        return true;
    }
};
```

### java

```java
public class Solution {
    
    int getCode(char ch){
        if (ch>='0' && ch<='9'){
            return ch;
        }
        if (ch>='A' && ch<='Z'){
            return ch +('a'-'A');
        }
        if (ch>='a' && ch<='z'){
            return ch;
        }
        return 0;
    }
    
    public boolean isPalindrome(String s) {
        int len = s.length();
        if (len<=1){
            return true;
        }
        char[] chs = s.toCharArray();
        int p = 0;
        int q = len -1;
        do{
            while (p<len && getCode(chs[p])==0){
                p++;
            }
            while (q>=0 && getCode(chs[q])==0){
                q--;
            }
            if (p<q && getCode(chs[p])!= getCode(chs[q])){
                return false;
            }
            p++;
            q--;
        }while (p<q);
        return true;
    }
}
```

### c

```c
int getCode(char ch){
    if (ch>='0' && ch<='9'){
        return ch;
    }
    if (ch>='A' && ch<='Z'){
        return ch +('a'-'A');
    }
    if (ch>='a' && ch<='z'){
        return ch;
    }
    return 0;
}

bool isPalindrome(char* s) {
    int len = strlen(s);
    if (len<=1){
        return true;
    }
    int p = 0;
    int q = len -1;
    do{
        while (p<len && !getCode(s[p])){
            p++;
        }
        while (q>=0 && !getCode(s[q])){
            q--;
        }
        if (p<q && getCode(s[p])!= getCode(s[q])){
            return false;
        }
        p++;
        q--;
    }while (p<q);
    return true;
}
```