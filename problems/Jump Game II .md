# Jump Game II

> [https://leetcode.com/problems/jump-game-ii/](https://leetcode.com/problems/jump-game-ii/)

## Tags

> [Array](../tags/Array.md)

> [Greedy](../tags/Greedy.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        int numsSize = nums.size();
        int start = 0;
        int end = 1;
        int step = 0;
        while (end< numsSize){
            int max = end;
            for (int i=start; i<end; i++){
                int loc = nums[i]+ i;
                if (loc>max){
                    max = loc;
                }
            }
            start = end;
            end = max+1;
            step++;
        }
        return step;
    }
};
```

### java

```java
public class Solution {
    public int jump(int[] nums) {
        int numsSize = nums.length;
        int start = 0;
        int end = 1;
        int step = 0;
        while (end< numsSize){
            int max = end;
            for (int i=start; i<end; i++){
                int loc = nums[i]+ i;
                if (loc>max){
                    max = loc;
                }
            }
            start = end;
            end = max+1;
            step++;
        }
        return step;
    }
}
```

### c

```c
int jump(int* nums, int numsSize) {
    int start = 0;
    int end = 1;
    int step = 0;
    while (end< numsSize){
        int max = end;
        for (int i=start; i<end; i++){
            int loc = nums[i]+ i;
            if (loc>max){
                max = loc;
            }
        }
        start = end;
        end = max+1;
        step++;
    }
    return step;
}
```