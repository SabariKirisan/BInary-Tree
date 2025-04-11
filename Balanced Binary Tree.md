## Balanced Binary Tree (c++)

Given a binary tree, determine if it is height-balanced.

## Example
![image](https://github.com/user-attachments/assets/773d4c54-d1db-4357-9b95-959ed29a0975)

Input: root = [1,2,2,3,3,null,null,4,4]

Output: false
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int check_height(TreeNode* root)
    {
        if(root == NULL) return 0;

        int lh=check_height(root->left);
        if(lh == -1) return -1;
        int rh=check_height(root->right);
        if(rh == -1) return -1;

        if(abs(lh-rh)>1) return -1;
        return max(lh,rh) +1;
    }
    bool isBalanced(TreeNode* root) 
    {
        return check_height(root) != -1;   
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
