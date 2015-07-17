# Longest Valid Parentheses

> [https://leetcode.com/problems/longest-valid-parentheses/](https://leetcode.com/problems/longest-valid-parentheses/)

## Tags

> [Dynamic Programming](../tags/Dynamic Programming.md)

> [String](../tags/String.md)

## Solutions

### cpp

```cpp
class Solution {
public:
    int longestValidParentheses(string s) {
        stack<int> stk;
        stk.push(-1);
        int max = 0;
        int len = s.length();
        for (int i=0; i<len; i++){
            if (s[i]=='('){
                stk.push(i);
            }else{
                if (stk.size()>1){
                    stk.pop();
                    int value = i- stk.top();
                    if (max < value){
                        max =value;
                    }
                }else{
                    stk.pop();
                    stk.push(i);
                }
            }
        }
        return max;
    }
};
```

### c

```c
struct node{
    int val;
    struct node* next;
};

struct stack{
    struct node* first;
    int size;
};

void stack_init(struct stack* s){
    s->first =malloc(sizeof(struct node));
    s->first->next = NULL;
    s->size = 0;
}

void stack_push(struct stack *s, int d){
    struct node * p = malloc(sizeof(struct node));
    p->val = d;
    p->next = s->first->next;
    s->first->next = p;
    s->size++;
}

void stack_pop(struct stack *s){
    struct node * p = s->first->next;
    s->first->next = p->next;
    free(p);
    s->size--;
}

int stack_top(struct stack* s){
    return s->first->next->val;
}

void stack_destory(struct stack *s){
    struct node *p  = s->first;
    while (p){
        struct node* q = p->next;
        free(p);
        p = q;
    }
}

int longestValidParentheses(char* s) {
    struct stack stk;
    stack_init(&stk);
    stack_push(&stk, -1);
    int max = 0;
    int len = strlen(s);
    for (int i=0; i<len; i++){
        if (s[i]=='('){
            stack_push(&stk, i);
        }else{
            if (stk.size>1){
                stack_pop(&stk);
                int value = i- stack_top(&stk);
                if (max < value){
                    max =value;
                }
            }else{
                stack_pop(&stk);
                stack_push(&stk, i);
            }
        }
    }
    stack_destory(&stk);
    return max;
}
```

### java

```java
public class Solution {
    public int longestValidParentheses(String s) {
        Stack<Integer> stack = new Stack<Integer>();
        stack.push(-1);
        char[] chs = s.toCharArray();
        int max = 0;
        for (int i=0; i<chs.length; i++){
            if (chs[i]=='('){
                stack.push(i);
            }else{
                if (stack.size()>1){
                    stack.pop();
                    int value = i- stack.peek();
                    if (max < value){
                        max =value;
                    }
                }else{
                    stack.pop();
                    stack.push(i);
                }
            }
        }
        return max;
    }
}
```