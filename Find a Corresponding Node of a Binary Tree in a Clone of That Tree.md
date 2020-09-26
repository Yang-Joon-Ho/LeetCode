[문제](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/)
----------

<br>
<br>

### 1. 코드 

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

    TreeNode * answer;
    
    void dfs(TreeNode * root, TreeNode * target) {
         
        if(root->val == target->val) {
            answer = root;
            return;
        }
        else if(root->left == NULL && root->right == NULL)
            return;
        
        if(root->left != NULL)
            dfs(root->left, target);
        if(root->right != NULL)
            dfs(root->right, target);
        
    }
    
    public:
    TreeNode* getTargetCopy(TreeNode* original, TreeNode* cloned, TreeNode* target) {
        
        dfs(cloned, target);
        
        return answer;
    }
};
```
