# Remove Linked List Elements

> [https://leetcode.com/problems/remove-linked-list-elements/](https://leetcode.com/problems/remove-linked-list-elements/)

## Tags

> [Linked List](../tags/Linked List.md)

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
    ListNode* removeElements(ListNode* head, int val) {
        struct ListNode *p  = head;
        while (p && p->val == val){
            struct ListNode *q = p;
            p = p->next;
            free(q);
        }
        if (p){
            struct ListNode* last = p;
            struct ListNode* current = p->next;
            while (current){
                if (current->val!=val){
                    last->next = current;
                    last = current;
                    current = current->next;
                }else{
                    struct ListNode * q = current;
                    current = current->next;
                    free(q);
                }
            }
            last->next = NULL;
            return p;
        }else{
            return NULL;
        }
    }
};
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
struct ListNode* removeElements(struct ListNode* head, int val) {
    struct ListNode *p  = head;
    while (p && p->val == val){
        struct ListNode *q = p;
        p = p->next;
        free(q);
    }
    if (p){
        struct ListNode* last = p;
        struct ListNode* current = p->next;
        while (current){
            if (current->val!=val){
                last->next = current;
                last = current;
                current = current->next;
            }else{
                struct ListNode * q = current;
                current = current->next;
                free(q);
            }
        }
        last->next = NULL;
        return p;
    }else{
        return NULL;
    }
}
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
    public ListNode removeElements(ListNode head, int val) {
        ListNode pp = null;
        ListNode p = head;
        ListNode q = head;
        while(q!=null){
            if (q.val!=val){
                p.val = q.val;
                pp = p;
                p = p.next;
            }
            q=q.next;
        }
        if (pp==null){
            return null;
        }else{
            pp.next = null;
            return head;
        }
    }
}
```