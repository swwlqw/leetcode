# Same Tree

> [https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)

## Tags

> [Tree](../tags/Tree.md)

> [Depth-first Search](../tags/Depth-first Search.md)

## Solutions

### cpp

```cpp
/**
 * Definition for binary tree
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode *p, TreeNode *q) {
        if (p==NULL && q ==NULL)
            return true;
        if (p!=NULL && q!=NULL){
            if (p->val != q->val)
                return false;
            if (!isSameTree(p->left, q->left))
                return false;
            if (!isSameTree(p->right, q->right))
                return false;
            return true;
        }   
        return false;
    }
};
```

### c

```c
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
bool isSameTree(struct TreeNode* p, struct TreeNode* q) {
    if (p==NULL && q ==NULL)
        return true;
    if (p!=NULL && q!=NULL){
        if (p->val != q->val)
            return false;
        if (!isSameTree(p->left, q->left))
            return false;
        if (!isSameTree(p->right, q->right))
            return false;
        return true;
    }   
    return false;
}
```

### java

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null){
            return q == null;
        }else{
            if (q == null){
                return false;
            }else {
                if (p.val == q.val){
                    return isSameTree(p.left, q.left) &&  isSameTree(p.right, q.right);
                }else{
                    return false;
                }
            }
        }
    }
}
```