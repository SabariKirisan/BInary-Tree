## Count Complete Tree Nodes (c++)

Given the root of a complete binary tree, return the number of the nodes in the tree.

According to Wikipedia, every level, except possibly the last, is completely filled in a complete binary tree, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.

Design an algorithm that runs in less than O(n) time complexity.

## Example
![image](https://github.com/user-attachments/assets/cfa7daa4-29a9-461c-a252-48a0f6a41705)

Input: root = [1,2,3,4,5,6]

Output: 6
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int count_left(TreeNode* root)
    {
        int height=0;
        while(root)
        {
            height++;
            root=root->left;
        }
        return height;
    }
    int count_right(TreeNode* root)
    {
        int height=0;
        while(root)
        {
            height++;
            root=root->right;
        }
        return height; 
    }
    int countNodes(TreeNode* root) 
    {
        if(root==NULL) return 0;

        int lh=count_left(root);
        int rh=count_right(root);

        if(lh==rh) return (1<<lh)-1;

        return 1+countNodes(root->left)+countNodes(root->right);
    }
};
```
## Complexity
- Time complexity : O(log N)^2 

- Space complexity : O(log N)
