# Min Stack

> [https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)

## Tags

> [Stack](../tags/Stack.md)

> [Data Structure](../tags/Data Structure.md)

## Solutions

### cpp

```cpp
class Node{
public:
    int data;
    int min;
    Node *next;
};

class MinStack {
public:
    Node* head;
    
    MinStack(){
        head = new Node();
        head->next = NULL;
    }
    
    ~MinStack(){
        while (head){
            Node *p = head;
            head = head->next;
            delete p;
        }
    }
    
    void push(int x) {
        Node *node = new Node();
        node->data = x;
        node->next = head->next;
        if (node->next){
            node->min = x <= node->next->min ? x : node->next->min;
        }else{
            node->min = x;
        }
        head->next = node;
    }

    void pop() {
        Node *p = head->next;
        head->next = head->next->next;
        delete p;
    }

    int top() {
        return head->next->data;
    }

    int getMin() {
        return head->next->min;
    }
};
```

### c

```c
typedef struct node{
    int data;
    int min;
    struct node* next;
} Node;

typedef struct {
    Node *head;
} MinStack;

void minStackCreate(MinStack *stack, int maxSize) {
    stack->head = malloc(sizeof(Node));
    stack->head->next = NULL;
}

void minStackPush(MinStack *stack, int element) {
    Node *node = malloc(sizeof(Node));
    node->data = element;
    node->next = stack->head->next;
    if (node->next){
        node->min = element <= node->next->min ? element : node->next->min;
    }else{
        node->min = element;
    }
    stack->head->next = node;
}

void minStackPop(MinStack *stack) {
    Node *p = stack->head->next;
    stack->head->next = p->next;
    free(p);
}

int minStackTop(MinStack *stack) {
    return stack->head->next->data;
}

int minStackGetMin(MinStack *stack) {
    return stack->head->next->min;
}

void minStackDestroy(MinStack *stack) {
    Node * p = stack->head;
    while (p){
        Node * del = p;
        p = p->next;
        free(del);
    }
}
```

### java

```java
class MinStack {
    
    static class Node{
        int data;
        int min;
        Node next;
    }
    
    Node head = new Node();
    
    public void push(int x) {
        Node node = new Node();
        node.data = x;
        node.next = head.next;
        if (node.next==null){
            node.min = x;
        }else{
            node.min = Math.min(x, node.next.min);
        }
        head.next = node;
    }

    public void pop() {
        head.next = head.next.next;
    }

    public int top() {
        return head.next.data;
    }

    public int getMin() {
        return head.next.min;
    }
}

```