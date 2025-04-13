## Binary Tree Right Side View (c++)

Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

## Example
Input: root = [1,2,3,4,null,null,null,5]

Output: [1,3,4,5]

Explanation:

![image](https://github.com/user-attachments/assets/7cdaf69b-ccc3-4d47-8d5c-43105649c3f6)


## PROGRAM:(Main.cpp)
```
class Solution {
public:
    vector<int> rightSideView(TreeNode* root) 
    {
        vector<int> res;
        recursion(root,0,res);
        return res;   
    }
    void recursion(TreeNode* root,int level,vector<int> &res)
    {
        if(root==NULL) return;
        if(level==res.size()) res.push_back(root->val);

        recursion(root->right,level+1,res);
        recursion(root->left,level+1,res);
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(H)
