# Excel Sheet Column Title

> [https://leetcode.com/problems/excel-sheet-column-title/](https://leetcode.com/problems/excel-sheet-column-title/)

## Tags

> [Math](../tags/Math.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    string convertToTitle(int n) {
        string re;
        while (n>0){
            int mod = n%26;
            int div = n/26;
            if (mod==0){
                re ='Z'+ re;
                n = div - 1;
            }else{
                char ch = (char)(mod-1+'A');
                re = ch + re;
                n = div;
            }
        }
        return re;
    }
};
```

### c

```c
char* convertToTitle(int n) {
    char * re = malloc(sizeof(char) * 20);
    re[19] = '\0';
    char *p = re + 18;
    while (n>0){
        int mod = n%26;
        int div = n/26;
        if (mod == 0){
            *p = 'Z';
            n = div -1;
        }else{
            char ch =(char) (mod-1+'A');
            *p = ch;
            n = div;
        }
        p--;
    }
    p++;
    return p;
}
```

### java

```java
public class Solution {
    public String convertToTitle(int n) {
        StringBuilder sb = new StringBuilder();
        while ( n > 0){
            int mod = n % 26;
            int div = n / 26;
            if (mod == 0){
                sb.append('Z');
                n = div - 1;
            }else{
                char ch = (char)(mod-1+'A');
                sb.append(ch);
                n = div;
            }
        }
        return sb.reverse().toString();
    }
}
```