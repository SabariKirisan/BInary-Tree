## Iterative Preorder Traversal of Binary Tree (c++)

Given the root of a binary tree, return the preorder traversal of its nodes' values.

## Example
Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]

Output: [4,2,6,5,7,1,3,9,8]

Explanation:

![image](https://github.com/user-attachments/assets/222ebd7d-520f-47d2-b1a0-0d4cc0a0d292)

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) 
    {
        vector<int> ans;
        if(root==NULL) return ans;
        stack<TreeNode*> st;
        st.push(root);

        while(!st.empty())
        {
            TreeNode* node=st.top();
            st.pop();
            ans.push_back(node->val);

            if(node->right!=NULL) st.push(node->right);
            if(node->left!=NULL) st.push(node->left);
        }
        return ans;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)

