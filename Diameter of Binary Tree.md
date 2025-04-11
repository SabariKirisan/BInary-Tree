## Diameter of Binary Tree (c++)

Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.

## Example
![image](https://github.com/user-attachments/assets/3a96e2da-50ec-4fce-b4f4-a67017409759)

Input: root = [1,2,3,4,5]

Output: 3

Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int height(TreeNode* root,int &diameter)
    {
        if(root==NULL) return 0;

        int lh=height(root->left,diameter);
        int rh=height(root->right,diameter);

        diameter=max(diameter,lh+rh);

        return 1+max(lh,rh);
    }
    int diameterOfBinaryTree(TreeNode* root) 
    {
        int diameter =0;
        height(root,diameter);
        return diameter;    
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
