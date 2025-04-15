
## Construct Binary Tree from Preorder and Inorder Traversal (c++)

Given two integer arrays preorder and inorder where preorder is the preorder traversal of a binary tree and inorder is the inorder traversal of the same tree, construct and return the binary tree.

## Example
![image](https://github.com/user-attachments/assets/0d3a885a-6171-41c5-bd72-275d33f50c93)

Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]

Output: [3,9,20,null,null,15,7]
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* build_tree(vector<int>& preorder,int pre_start,int pre_end,vector<int>& inorder,int in_start,int in_end,map<int,int> &in_mpp)
    {
        if(pre_start>pre_end || in_start>in_end ) return NULL;

        TreeNode* root=new TreeNode(preorder[pre_start]);

        int inroot=in_mpp[root->val];
        int nums_left=inroot-in_start;

        root->left=build_tree(preorder,pre_start+1,pre_end+nums_left,inorder,in_start,inroot-1,in_mpp);

        root->right=build_tree(preorder,pre_start+nums_left+1,pre_end,inorder,inroot+1,in_end,in_mpp);

        return root;
    }

    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) 
    {
        map<int,int> in_mpp;
        for(int i=0;i<inorder.size();i++)
        {
            in_mpp[inorder[i]]=i;
        }   
        TreeNode* root=build_tree(preorder,0,preorder.size()-1,inorder,0,inorder.size()-1,in_mpp);
        
        return root;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
