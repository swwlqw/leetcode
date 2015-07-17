# Two Sum

> [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

## Tags

> [Array](../tags/Array.md)

> [Hash Table](../tags/Hash Table.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> m;
        vector<int> re;
        int size = nums.size();
        for(int i=0; i<size; i++){
            int num = nums[i];
            int last = target - num;
            map<int,int>::iterator it = m.find(last);
            if (it != m.end()){
                int sm = it->second;
                re.push_back(sm+1);
                re.push_back(i+1);
                return re;
            }else{
                m[num] = i;
            }
        }
        return re;
    }
};
```

### c

```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
typedef struct node{
    int key;
    int value;
    struct node* next;
} Node;

typedef struct list{
    Node first;
} List;

typedef struct map{
    List* lists;
    int size;
} Map;

void map_init(Map* map, int size){
    map->size = size;
    int len = sizeof(List) * size;
    map->lists = malloc(len);
    memset(map->lists, 0, len);
}

Node* map_contains(Map* map, int key){
    int mod = key % map->size;
    if (mod < 0){
        mod += map->size;
    }
    List* list = &(map->lists[mod]);
    Node* p = list->first.next;
    while (p){
        if (p->key == key){
            return p;
        }
        p = p->next;
    }
    return NULL;
}

Node* map_put(Map* map, int key, int value){
    int mod = key % map->size;
    if (mod < 0){
        mod += map->size;
    }
    List* list = &(map->lists[mod]);
    Node * node = malloc(sizeof(Node));
    node->key = key;
    node->value = value;
    node->next = list->first.next;
    list->first.next = node;
    return 0;
}

void map_destory(Map* map){
    int size = map->size;
    for (int i=0; i<size; i++){
        List* list = &(map->lists[i]);
        Node *p = list->first.next;
        while (p){
            Node *next = p->next;
            free(p);
            p = next;
        }
    }
    free(map->lists);
}

int* twoSum(int* nums, int numsSize, int target) {
    Map map;
    map_init(&map, numsSize * 2 + 1);
    for (int i=0; i<numsSize; i++){
        int num = nums[i];
        Node * node = map_contains(&map, target-num);
        if (node){
            int * re = malloc(sizeof(int)*2);
            re[0] = node->value+1;
            re[1] = i+1;
            map_destory(&map);
            return re;
        }else{
            map_put(&map, num, i);
        }
    }
    map_destory(&map);
    return NULL;
}
```

### java

```java
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer> map = new HashMap<Integer,Integer>();
        for (int i=0; i<nums.length; i++){
            map.put(nums[i], i);
        }
        for (int i=0; i<nums.length; i++){
            int next = target - nums[i];
            Integer index = map.get(next);
            if (index != null && index != i){
                int[] re = new int[2];
                re[0] = i+1;
                re[1] = index+1;
                return re;
            }
        }
        return null;
    }
}
```