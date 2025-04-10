## Maximum Depth of Binary Tree (c++)

Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

## Example
![image](https://github.com/user-attachments/assets/2234b6c3-f643-4ba2-921a-7263da701c41)

Input: root = [3,9,20,null,null,15,7]

Output: 3

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int maxDepth(TreeNode* root) 
    {
        if(root==NULL) return 0;

        int lh=maxDepth(root->left);
        int rh=maxDepth(root->right);

        return 1+max(lh,rh);    
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
