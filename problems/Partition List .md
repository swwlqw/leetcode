# Partition List

> [https://leetcode.com/problems/partition-list/](https://leetcode.com/problems/partition-list/)

## Tags

> [Linked List](../tags/Linked List.md)

> [Two Pointers](../tags/Two Pointers.md)

## Solutions

### cpp

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* partition(ListNode* head, int x) {
        ListNode p1(0);
        ListNode p2(0);
        ListNode* l1 = &p1;
        ListNode* l2 = &p2;
        ListNode* p = head;
        while (p){
            if (p->val< x){
                l1->next = p;
                l1 = p;
            }else{
                l2->next = p;
                l2 = p;
            }
            p = p->next;
        }
        l1->next = p2.next;
        l2->next = NULL;
        return p1.next;
    }
};
```

### java

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode partition(ListNode head, int x) {
        ListNode p1 = new ListNode(0);
        ListNode p2 = new ListNode(0);
        ListNode l1 = p1;
        ListNode l2 = p2;
        ListNode p = head;
        while (p!=null){
            if (p.val< x){
                l1.next = p;
                l1 = p;
            }else{
                l2.next = p;
                l2 = p;
            }
            p = p.next;
        }
        l1.next = p2.next;
        l2.next = null;
        return p1.next;
    }
}
```

### c

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct List{
    struct ListNode first;
    struct ListNode *last;
};

struct ListNode* partition(struct ListNode* head, int x) {
    struct List less;
    struct List greater;
    less.last = &(less.first);
    greater.last = &(greater.first);
    struct ListNode * p = head;
    while (p){
        if (p->val <x){
            less.last->next = p;
            less.last = p;
        }else{
            greater.last->next = p;
            greater.last = p;
        }
        p = p->next;
    }
    greater.last->next = NULL;
    less.last->next = greater.first.next;
    return less.first.next;
}
```