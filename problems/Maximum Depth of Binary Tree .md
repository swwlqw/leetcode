# Maximum Depth of Binary Tree

> [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

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
    int maxDepth(TreeNode *root) {
        if (root==NULL){
            return 0;
        }
        if (root->left==NULL && root->right==NULL){
            return 1;
        }
        int l = maxDepth(root->left);
        int r = maxDepth(root->right);
        if (l>r){
            return l+1;
        }
        return r+1;
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
int maxDepth(struct TreeNode* root) {
    if (root==NULL){
        return 0;
    }
    int l = maxDepth(root->left);
    int r = maxDepth(root->right);
    if (l>r){
        return l+1;
    }
    return r+1;
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
    public int maxDepth(TreeNode root) {
        if (root == null){
            return 0;
        }
        int left = maxDepth(root.left);
        int right = maxDepth(root.right);
        if (left < right){
            return right + 1;
        }else{
            return left + 1;
        }
    }
}
```