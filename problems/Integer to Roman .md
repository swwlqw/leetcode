# Integer to Roman

> [https://leetcode.com/problems/integer-to-roman/](https://leetcode.com/problems/integer-to-roman/)

## Tags

> [Math](../tags/Math.md)

> [String](../tags/String.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    string intToRoman(int num) {
        char chs[4][2] = {
            'I','V',
            'X','L',
            'C','D',
            'M','Q'
        };
        stringstream ss;
        ss<<num;
        string str = ss.str();
        int len = str.length();
        string re;
        for (int i=len-1; i>=0; i--){
            int val = str.at(len-1-i)-'0';
            switch(val){
                case 1:
                    re+=(chs[i][0]);
                    break;
                case 2:
                    re+=(chs[i][0]);
                    re+=(chs[i][0]);
                    break;
                case 3:
                    re+=(chs[i][0]);
                    re+=(chs[i][0]);
                    re+=(chs[i][0]);
                    break;
                case 4:
                    re+=(chs[i][0]);
                    re+=(chs[i][1]);
                    break;
                case 5:
                    re+=(chs[i][1]);
                    break;
                case 6:
                    re+=(chs[i][1]);
                    re+=(chs[i][0]);
                    break;
                case 7:
                    re+=(chs[i][1]);
                    re+=(chs[i][0]);
                    re+=(chs[i][0]);
                    break;
                case 8:
                    re+=(chs[i][1]);
                    re+=(chs[i][0]);
                    re+=(chs[i][0]);
                    re+=(chs[i][0]);
                    break;
                case 9:
                    re+=(chs[i][0]);
                    re+=(chs[i+1][0]);
                    break;
            }
        }
        return re;
    }
};
```

### c

```c
char* intToRoman(int num) {
    char chs[4][2] = {
        'I','V',
        'X','L',
        'C','D',
        'M','Q'
    };
    char str[5];
    sprintf(str,"%d", num);
    int len = strlen(str);
    int index =0;
    char * re = malloc(sizeof(char)*20);
    for (int i=len-1; i>=0; i--){
        int val = str[len-1-i]-'0';
        switch(val){
            case 1:
                re[index++]=(chs[i][0]);
                break;
            case 2:
                re[index++]=(chs[i][0]);
                re[index++]=(chs[i][0]);
                break;
            case 3:
                re[index++]=(chs[i][0]);
                re[index++]=(chs[i][0]);
                re[index++]=(chs[i][0]);
                break;
            case 4:
                re[index++]=(chs[i][0]);
                re[index++]=(chs[i][1]);
                break;
            case 5:
                re[index++]=(chs[i][1]);
                break;
            case 6:
                re[index++]=(chs[i][1]);
                re[index++]=(chs[i][0]);
                break;
            case 7:
                re[index++]=(chs[i][1]);
                re[index++]=(chs[i][0]);
                re[index++]=(chs[i][0]);
                break;
            case 8:
                re[index++]=(chs[i][1]);
                re[index++]=(chs[i][0]);
                re[index++]=(chs[i][0]);
                re[index++]=(chs[i][0]);
                break;
            case 9:
                re[index++]=(chs[i][0]);
                re[index++]=(chs[i+1][0]);
                break;
        }
    }
    re[index++]='\0';
    return re;
}
```

### java

```java
public class Solution {
    public String intToRoman(int num) {
        char[][] chs = new char[][]{
            {'I','V'},
            {'X','L'},
            {'C','D'},
            {'M','Q'}
        };
        String str = num + "";
        int len = str.length();
        StringBuilder sb = new StringBuilder();
        for (int i=len-1; i>=0; i--){
            int val = str.charAt(len-1-i)-'0';
            switch(val){
                case 1:
                    sb.append(chs[i][0]);
                    break;
                case 2:
                    sb.append(chs[i][0]);
                    sb.append(chs[i][0]);
                    break;
                case 3:
                    sb.append(chs[i][0]);
                    sb.append(chs[i][0]);
                    sb.append(chs[i][0]);
                    break;
                case 4:
                    sb.append(chs[i][0]);
                    sb.append(chs[i][1]);
                    break;
                case 5:
                    sb.append(chs[i][1]);
                    break;
                case 6:
                    sb.append(chs[i][1]);
                    sb.append(chs[i][0]);
                    break;
                case 7:
                    sb.append(chs[i][1]);
                    sb.append(chs[i][0]);
                    sb.append(chs[i][0]);
                    break;
                case 8:
                    sb.append(chs[i][1]);
                    sb.append(chs[i][0]);
                    sb.append(chs[i][0]);
                    sb.append(chs[i][0]);
                    break;
                case 9:
                    sb.append(chs[i][0]);
                    sb.append(chs[i+1][0]);
                    break;
            }
        }
        return sb.toString();
    }
}
```