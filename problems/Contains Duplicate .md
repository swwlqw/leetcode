# Contains Duplicate

> [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

## Tags

> [Array](../tags/Array.md)

> [Hash Table](../tags/Hash Table.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        set<int> s;
        for (vector<int>::iterator it = nums.begin(); it!=nums.end(); ++it){
            int num = *it;
            if (s.find(num)!=s.end()){
                return true;
            }
            s.insert(num);
        }
        return false;
    }
};
```

### c

```c
typedef struct node{
    int val;
    struct node* next;
} Node;

typedef struct list{
    Node first;
} List;

typedef struct set{
    List* lists;
    int size;
} Set;

void set_init(Set* set, int size){
    set->size = size;
    int len = sizeof(List) * size;
    set->lists = malloc(len);
    memset(set->lists, 0, len);
}

int set_put(Set* set, int val){
    int mod = val % set->size;
    if (mod < 0){
        mod += set->size;
    }
    List* list = &(set->lists[mod]);
    Node* p = list->first.next;
    while (p){
        if (p->val == val){
            return 1;
        }
        p = p->next;
    }
    Node * node = malloc(sizeof(Node));
    node->val = val;
    node->next = list->first.next;
    list->first.next = node;
    return 0;
}

void set_destory(Set* set){
    int size = set->size;
    for (int i=0; i<size; i++){
        List* list = &(set->lists[i]);
        Node *p = list->first.next;
        while (p){
            Node *next = p->next;
            free(p);
            p = next;
        }
    }
    free(set->lists);
}

bool containsDuplicate(int* nums, int numsSize) {
    Set set;
    set_init(&set, numsSize * 2 + 1);
    for (int i=0;i<numsSize;i++){
        if (set_put(&set, nums[i])){
            set_destory(&set);
            return true;
        }
    }
    set_destory(&set);
    return false;
}
```

### java

```java
public class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<Integer>(nums.length*2);
        for (int num : nums){
            if (set.contains(num)){
                return true;
            }
            set.add(num);
        }
        return false;
    }
}
```