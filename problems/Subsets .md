# Subsets

> [https://leetcode.com/problems/subsets/](https://leetcode.com/problems/subsets/)

## Tags

> [Array](../tags/Array.md)

> [Backtracking](../tags/Backtracking.md)

> [Bit Manipulation](../tags/Bit Manipulation.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<int> v;
        vector<vector<int>> re;
        re.push_back(v);
        for (vector<int>::iterator it = nums.begin(); it!= nums.end(); ++it){
            int num = *it;
            int size = re.size();
            for (int i=0; i<size; i++){
                vector<int> nv = re[i];
                nv.push_back(num);
                re.push_back(nv);
            }
        }
        return re;
    }
};
```

### c

```c
/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *columnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int cmp(const void *a, const void *b)
{
    return *(int *)a - *(int *)b;
}

int** subsets(int* nums, int numsSize, int** columnSizes, int* returnSize) {
    qsort(nums, numsSize, sizeof(int), cmp);
    int size = 1 << numsSize;
    *returnSize = size;
    *columnSizes = malloc(size* sizeof(int));
    int* cs = *columnSizes;
    int** re = malloc(size*(sizeof(int*))); 
    cs[0] = 0;
    re[0] = malloc(0);
    int index = 1;
    for (int i=0; i<numsSize;i++){
        int num =nums[i];
        int now = index;
        for (int j=0;j<now;j++){
            cs[index] = cs[j]+1;
            re[index] = malloc(cs[index] * sizeof(int));
            memcpy(re[index], re[j], cs[j] * sizeof(int));
            re[index][cs[j]] = num;
            index++;
        }
    }
    return re;
}
```

### java

```java
public class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        Arrays.sort(nums);
		List<List<Integer>> list = new ArrayList<List<Integer>>();
		List<Integer> empty = new ArrayList<Integer>();
		list.add(empty);
		for (int num : nums) {
			int size = list.size();
			for (int j = 0; j < size; j++) {
				ArrayList<Integer> datas = (ArrayList<Integer>) list.get(j);
				List<Integer> newDatas = (List<Integer>) datas.clone();
				newDatas.add(num);
				list.add(newDatas);
			}
		}
		return list;
    }
}
```