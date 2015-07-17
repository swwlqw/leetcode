# Length of Last Word

> [https://leetcode.com/problems/length-of-last-word/](https://leetcode.com/problems/length-of-last-word/)

## Tags

> [String](../tags/String.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int len = s.length();
        int re = 0;
        for (int i=len-1; i>=0; i--){
            if (s[i] == ' '){
                if (re>0){
                    return re;
                }
            }else{
                re++;
            }
        }
        return re;
    }
};
```

### c

```c
int lengthOfLastWord(char* s) {
    int len = strlen(s);
    int re = 0;
    for (int i=len-1; i>=0; i--){
        if (s[i] == ' '){
            if (re>0){
                return re;
            }
        }else{
            re++;
        }
    }
    return re;
}
```

### java

```java
public class Solution {
    public int lengthOfLastWord(String s) {
        char[] chs = s.toCharArray();
        int re = 0;
        for (int i=chs.length-1; i>=0; i--){
            char ch = chs[i];
            if (ch==' '){
                if (re>0){
                    return re;
                }
            }else{
                re++;
            }
        }
        return re;
    }
}
```