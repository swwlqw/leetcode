# Text Justification

> [https://leetcode.com/problems/text-justification/](https://leetcode.com/problems/text-justification/)

## Tags

> [String](../tags/String.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    string calString(vector<string>& temp, int size, int maxWidth){
        string sb;
        if (temp.size()==1){
            sb += temp[0];
            int ch = maxWidth - sb.length();
            for (int i=0; i<ch; i++){
                sb += ' ';
            }
        }else{
            int ch = maxWidth - size;
            int period = temp.size()-1;
            int div = ch/period;
            int mod = ch%period;
            for (int i=0; i<period; i++){
                sb += temp[i];
                int num = div+1;
                if (mod>i)
                    num++;
                for (int j=0;j<num; j++){
                    sb += ' ';
                }
            }
            sb+= temp[period];
        }
        return sb;
    }
    vector<string> fullJustify(vector<string>& words, int maxWidth) {
        vector<string> list;
        vector<string> temp;
        int size = -1;
        for (vector<string>::iterator it = words.begin(); it!=words.end(); ++it){
            string word = *it;
            int len = word.length();
            int newSize = size + len +1;
            if (newSize> maxWidth){
                list.push_back(calString(temp, size, maxWidth));
                temp.clear();
                temp.push_back(word);
                size = len;
            }else{
                size = newSize;
                temp.push_back(word);
            }
        }
        if (!temp.empty()){
            string sb;
            for (vector<string>::iterator it = temp.begin(); it!=temp.end(); ++it){
                sb += *it;
                sb += ' ';
            }
            int ch = maxWidth - sb.length();
            if (ch>0){
                for (int i=0; i<ch;i++){
                    sb += ' ';
                }
            }else if (ch<0){
                sb = sb.substr(0, maxWidth);
            }
            list.push_back(sb);
        }
        return list;
    }
};
```

### c

```c
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
char** fullJustify(char** words, int wordsSize, int maxWidth, int* returnSize) {
    char** re = malloc(sizeof(char*) * wordsSize);
    *returnSize = 0;
    int start = 0;
    int end = 0;
    int size = -1;
    int lens[wordsSize];
    for (int i=0; i<wordsSize;i++){
        lens[i] = strlen(words[i]);
        int newSize = lens[i] + size + 1;
        if (newSize>maxWidth){
            int number = end - start;
            char * str = malloc(maxWidth+1);
            re[*returnSize] = str;
            (*returnSize) ++;
            str[maxWidth] = '\0';
            memset(str, ' ', maxWidth);
            if (number==1){
                strncpy(str, words[start], lens[start]);
            }else{
                int period = number-1;
                int left = maxWidth - size;
                int div = left / period;
                int mod = left % period;
                
                char *p = str;
                for (int k= start; k<end; k++){
                    strncpy(p, words[k], lens[k]);
                    int add = lens[k] + div + 1;
                    if (k - start < mod){
                        add++;
                    }
                    p += add;
                }
            }
            start = i;
            end = i+1;
            size = lens[i];
        }else{
            size = newSize;
            end++;
        }
    }
    
    if (start<wordsSize){
        char * str = malloc(maxWidth+1);
        re[*returnSize] = str;
        (*returnSize) ++;
        memset(str, ' ', maxWidth);
        char * p = str;
        for (int k= start; k<wordsSize; k++){
            strncpy(p, words[k], lens[k]);
            p += (1+ lens[k]);
        }
        str[maxWidth] = '\0';
    }
    return re;
}
```

### java

```java
public class Solution {
    private String calString(List<String> temp, int size, int maxWidth){
        StringBuilder sb = new StringBuilder();
        if (temp.size()==1){
            sb.append(temp.get(0));
            int ch = maxWidth - sb.length();
            for (int i=0; i<ch; i++){
                sb.append(' ');
            }
        }else{
            int ch = maxWidth - size;
            int period = temp.size()-1;
            int div = ch/period;
            int mod = ch%period;
            for (int i=0; i<period; i++){
                sb.append(temp.get(i));
                int num = div+1;
                if (mod>i)
                    num++;
                for (int j=0;j<num; j++){
                    sb.append(' ');
                }
            }
            sb.append(temp.get(period));
        }
        return sb.toString();
    }
    
    public List<String> fullJustify(String[] words, int maxWidth) {
        List<String> list = new LinkedList<String>();
        List<String> temp = new ArrayList<String>();
        int size = -1;
        for (String word: words){
            int len = word.length();
            int newSize = size + len +1;
            if (newSize> maxWidth){
                list.add(calString(temp, size, maxWidth));
                temp.clear();
                temp.add(word);
                size = len;
            }else{
                size = newSize;
                temp.add(word);
            }
        }
        if (!temp.isEmpty()){
            StringBuilder sb = new StringBuilder();
            for (String str: temp){
                sb.append(str);
                sb.append(' ');
            }
            int ch = maxWidth - sb.length();
            if (ch>0){
                for (int i=0; i<ch;i++){
                    sb.append(' ');
                }
            }else if (ch<0){
                sb.setLength(maxWidth);
            }
            list.add(sb.toString());
        }
        return list;
    }
}
```