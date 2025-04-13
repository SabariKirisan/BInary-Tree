## Symmetric Tree (c++)

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

## Example
![image](https://github.com/user-attachments/assets/5dcb9aa2-38a2-4b1c-a6dc-cb7d5b7de6bb)

Input: root = [1,2,2,3,4,4,3]

Output: true

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool isSymmetric(TreeNode* root) 
    {
        return root==NULL || check(root->left,root->right);   
    }
    bool check(TreeNode* left,TreeNode* right)
    {
        if(left==NULL || right==NULL)
        {
            return left==right;
        }
        if(left->val!=right->val)
        {
            return false;
        }
        return check(left->right,right->left) && check(left->left,right->right);
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
