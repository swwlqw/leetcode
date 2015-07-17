# Jump Game

> [https://leetcode.com/problems/jump-game/](https://leetcode.com/problems/jump-game/)

## Tags

> [Array](../tags/Array.md)

> [Greedy](../tags/Greedy.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int ok = nums.size()-1;
        for (int i=ok-1; i>=0; i--){
            int sum = nums[i]+i;
            if (sum>=ok){
                ok = i;
            }
        }
        return ok==0;
    }
};
```

### c

```c
bool canJump(int* nums, int numsSize) {
    int ok = numsSize-1;
    for (int i=ok-1; i>=0; i--){
        int sum = nums[i]+i;
        if (sum>=ok){
            ok = i;
        }
    }
    return ok==0;
}
```

### java

```java
public class Solution {
    public boolean canJump(int[] nums) {
        int ok = nums.length-1;
        for (int i=ok-1; i>=0; i--){
            int sum = nums[i]+i;
            if (sum>=ok){
                ok = i;
            }
        }
        return ok==0;
    }
}
```

### javascript

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var canJump = function(nums) {
    var ok = nums.length-1;
    for (var i=ok-1; i>=0; i--){
        var sum = nums[i]+i;
        if (sum>=ok){
            ok = i;
        }
    }
    return ok===0;
};
```