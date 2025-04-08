## Binary Tree Preorder Traversal (c++)

Given the root of a binary tree, return the preorder traversal of its nodes' values.

## Example
Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]

Output: [1,2,4,5,6,7,3,8,9]

Explanation: 

![image](https://github.com/user-attachments/assets/feba273c-6f80-405f-a191-efd819a86750)


## PROGRAM:(Main.cpp)
```
class Solution {
public:
    void helper(TreeNode* root, vector<int>& ans) 
    { 
        if (!root) return;
        ans.push_back(root->val);      
        helper(root->left, ans);         
        helper(root->right, ans);    
    }

    vector<int> preorderTraversal(TreeNode* root) 
    {
        vector<int> ans;
        helper(root, ans);
        return ans;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)

