## Morris Binary Tree Inorder Traversal (c++)

Given the root of a binary tree, return the inorder traversal of its nodes' values.

## Example
Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]

Output: [4,2,6,5,7,1,3,9,8]

![image](https://github.com/user-attachments/assets/90db778e-9222-4c9a-8d89-ca43bb155fb6)

## PROGRAM:(Main.cpp)
```
class Solution 
{
public:
    vector<int> inorderTraversal(TreeNode* root) 
    {
        vector<int> ans;
        TreeNode* node=root;

        while(node!=NULL)
        {
            if(node->left==NULL)
            {
                ans.push_back(node->val);
                node=node->right;
            }
            else
            {
                TreeNode* prev=node->left;
                while(prev->right && prev->right!=node)
                {
                    prev=prev->right; 
                }
                if(prev->right==NULL)
                {
                    prev->right=node;
                    node=node->left;
                }
                else
                {
                    prev->right=NULL;
                    ans.push_back(node->val);
                    node=node->right;
                }
            }
        }
        return ans;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)
