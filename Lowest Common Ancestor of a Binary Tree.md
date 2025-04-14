## Lowest Common Ancestor of a Binary Tree (c++)

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”

## Example
![image](https://github.com/user-attachments/assets/72da1a6a-d1f0-4901-b3b4-089a5a69273a)

Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1

Output: 3

Explanation: The LCA of nodes 5 and 1 is 3.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q)  {
        if(root==NULL || root==p || root==q)
        {
            return root;
        }   
        TreeNode* left=lowestCommonAncestor(root->left,p,q);
        TreeNode* right=lowestCommonAncestor(root->right,p,q);

        if(left==NULL) return right;
        else if(right==NULL) return left;
        else return root;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
