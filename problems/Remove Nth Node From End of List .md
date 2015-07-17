# Remove Nth Node From End of List

> [https://leetcode.com/problems/remove-nth-node-from-end-of-list/](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* p = head;
        ListNode* q = head;
        for (int i=0; i< n; i++){
            p = p->next;
        }
        if (!p) { /** delete head **/
            ListNode* re = head->next;
            free(head);
            return re;
        }else{
            p = p->next;
            while (p){
                p = p->next;
                q = q->next;
            }
            ListNode* d = q->next;
            q->next = d->next;
            free(d);
            return head;
        }
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode p = head;
        ListNode q = head;
        for (int i=0; i< n; i++){
            p = p.next;
        }
        if (p == null) { /** delete head **/
            return head.next;
        }else{
            p = p.next;
            while (p!=null){
                p = p.next;
                q = q.next;
            }
            ListNode d = q.next;
            q.next = d.next;
            return head;
        }
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
struct ListNode* removeNthFromEnd(struct ListNode* head, int n) {
    struct ListNode* p = head;
    struct ListNode* q = head;
    for (int i=0; i< n; i++){
        p = p->next;
    }
    if (!p) { /** delete head **/
        struct ListNode* re = head->next;
        free(head);
        return re;
    }else{
        p = p->next;
        while (p){
            p = p->next;
            q = q->next;
        }
        struct ListNode* d = q->next;
        q->next = d->next;
        free(d);
        return head;
    }
}
```