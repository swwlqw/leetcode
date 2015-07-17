# Count Complete Tree Nodes

> [https://leetcode.com/problems/count-complete-tree-nodes/](https://leetcode.com/problems/count-complete-tree-nodes/)

## Tags

> [Tree](../tags/Tree.md)

> [Binary Search](../tags/Binary Search.md)

## Solutions

### cpp

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int exists(TreeNode* root, int index, int level){
        TreeNode * p = root;
        for (int i=level-2; i>=0; i--){
            int t = 1 << i;
            if (t & index){
                p = p->right;
            }else{
                p = p->left;
            }
        }
        if (p){
            return 1;
        }else{
            return 0;
        }
    }
    int countNodes(TreeNode* root) {
        if (root == NULL){
            return 0;
        }
        int level = 0;
        TreeNode *p= root;
        while (p){
            level++;
            p = p->left;
        }
        int left = 1<< (level -1);
        int right = (1<< level) - 1;
        if (exists(root, right, level)){
            return right;
        }
        while (left< right-1){
            int mid = (left+right)/2;
            if (exists(root, mid, level)){
                left = mid;
            }else{
                right = mid;
            }
        }
        return left;
    }
};
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
    boolean exists(TreeNode root, int index, int level){
        TreeNode p = root;
        for (int i=level-2; i>=0; i--){
            int t = 1 << i;
            if ((t & index) != 0){
                p = p.right;
            }else{
                p = p.left;
            }
        }
        return p!=null;
    }
    
    public int countNodes(TreeNode root) {
        if (root == null){
            return 0;
        }
        int level = 0;
        TreeNode p= root;
        while (p != null){
            level++;
            p = p.left;
        }
        int left = 1<< (level -1);
        int right = (1<< level) - 1;
        if (exists(root, right, level)){
            return right;
        }
        while (left< right-1){
            int mid = (left+right)/2;
            if (exists(root, mid, level)){
                left = mid;
            }else{
                right = mid;
            }
        }
        return left;
    }
}
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
 
int exists(struct TreeNode* root, int index, int level){
    struct TreeNode * p = root;
    for (int i=level-2; i>=0; i--){
        int t = 1 << i;
        if (t & index){
            p = p->right;
        }else{
            p = p->left;
        }
    }
    return p;
}
int countNodes(struct TreeNode* root) {
    if (root == NULL){
        return 0;
    }
    int level = 0;
    struct TreeNode *p= root;
    while (p){
        level++;
        p = p->left;
    }
    int left = 1<< (level -1);
    int right = (1<< level) - 1;
    if (exists(root, right, level)){
        return right;
    }
    while (left< right-1){
        int mid = (left+right)/2;
        if (exists(root, mid, level)){
            left = mid;
        }else{
            right = mid;
        }
    }
    return left;
}
```