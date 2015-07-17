# Edit Distance

> [https://leetcode.com/problems/edit-distance/](https://leetcode.com/problems/edit-distance/)

## Tags

> [Dynamic Programming](../tags/Dynamic Programming.md)

> [String](../tags/String.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int minDistance(string word1, string word2) {
        int len1 = word1.length();
        int len2 = word2.length();
        int f[len1+1][len2+1];
        for (int i=0;i<= len1;i++){
            f[i][0]=i;
        }
        for (int i=0;i<=len2;i++){
            f[0][i]= i;
        }
        for (int i=1;i<=len1;i++){
            char ch1 = word1.at(i-1);
            for (int j=1; j<=len2;j++){
                char ch2 = word2.at(j-1);
                if (ch1==ch2){
                    f[i][j] = f[i-1][j-1];
                }else{
                    int min = f[i][j-1] < f[i-1][j] ? f[i][j-1]: f[i-1][j];
                    min = min < f[i-1][j-1] ? min : f[i-1][j-1];
                    f[i][j] = min + 1;
                }
            }
        }
        return f[len1][len2];
    }
};
```

### c

```c
int min(int a, int b){
    if (a<b)
        return a;
    return b;
}
int minDistance(char* word1, char* word2) {
    int len1 = strlen(word1);
    int len2 = strlen(word2);
    int f[len1+1][len2+1];
    for (int i=0;i<= len1;i++){
        f[i][0]=i;
    }
    for (int i=0;i<=len2;i++){
        f[0][i]= i;
    }
    for (int i=1;i<=len1;i++){
        char ch1 = word1[i-1];
        for (int j=1; j<=len2;j++){
            char ch2 = word2[j-1];
            if (ch1==ch2){
                f[i][j] = f[i-1][j-1];
            }else{
                int last = min(f[i][j-1], f[i-1][j]);
                last = min(last, f[i-1][j-1]);
                f[i][j] = last + 1;
            }
        }
    }
    return f[len1][len2];
}
```

### java

```java
public class Solution {
    public int minDistance(String word1, String word2) {
        int len1 = word1.length();
        int len2 = word2.length();
        int[][] f = new int[len1+1][len2+1];
        for (int i=0;i<= len1;i++){
            f[i][0]=i;
        }
        for (int i=0;i<=len2;i++){
            f[0][i]= i;
        }
        for (int i=1;i<=len1;i++){
            char ch1 = word1.charAt(i-1);
            for (int j=1; j<=len2;j++){
                char ch2 = word2.charAt(j-1);
                if (ch1==ch2){
                    f[i][j] = f[i-1][j-1];
                }else{
                    int min = Math.min(f[i][j-1], f[i-1][j]);
                    min = Math.min(min, f[i-1][j-1]);
                    f[i][j] = min + 1;
                }
            }
        }
        return f[len1][len2];
    }
}
```