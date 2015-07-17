# Add Two Numbers

> [https://leetcode.com/problems/add-two-numbers/](https://leetcode.com/problems/add-two-numbers/)

## Tags

> [Linked List](../tags/Linked List.md)

> [Math](../tags/Math.md)

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode *first = new ListNode(0);
        ListNode *last = first;
        int div = 0;
        while (l1 || l2 || div){
            int sum = div;
            if (l1){
                sum += l1->val;
                l1 = l1->next;
            }
            if (l2){
                sum += l2->val;
                l2 = l2->next;
            }
            div = sum /10;
            int mod = sum % 10;
            ListNode *node = new ListNode(mod);
            last->next = node;
            last = node;
        }
        if (first == last){
            return first;
        }else{
            ListNode* re = first->next;
            delete first;
            return re;
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode first = new ListNode(0);
        ListNode last = first;
        int div = 0;
        while (l1!=null || l2!=null || div>0){
            int sum = div;
            if (l1!=null){
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2!=null){
                sum += l2.val;
                l2 = l2.next;
            }
            div = sum /10;
            int mod = sum % 10;
            ListNode node = new ListNode(mod);
            last.next = node;
            last = node;
        }
        if (first == last){
            return first;
        }else{
            return first.next;
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
struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode *first = malloc(sizeof(struct ListNode));
    struct ListNode *last = first;
    int div = 0;
    while (l1 || l2 || div){
        int sum = div;
        if (l1){
            sum += l1->val;
            l1 = l1->next;
        }
        if (l2){
            sum += l2->val;
            l2 = l2->next;
        }
        div = sum /10;
        int mod = sum % 10;
        struct ListNode *node = malloc(sizeof(struct ListNode));
        node->val = mod;
        last->next = node;
        last = node;
    }
    last->next = NULL;
    if (first == last){
        first -> val = 0;
        return first;
    }else{
        struct ListNode* re = first->next;
        free(first);
        return re;
    }
}
```