## Construct Binary Tree from Inorder and Postorder Traversal (c++)

Given two integer arrays inorder and postorder where inorder is the inorder traversal of a binary tree and postorder is the postorder traversal of the same tree, construct and return the binary tree.

## Example
![image](https://github.com/user-attachments/assets/3b7bb245-8222-4e83-a15c-27d866c361ee)

Input: inorder = [9,3,15,20,7], postorder = [9,15,7,20,3]

Output: [3,9,20,null,null,15,7]
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* build_tree(vector<int>& inorder,int in_start,int in_end,vector<int>& postorder,int pos_start,int pos_end,map<int,int> &in_mpp)
    {
        if(pos_start>pos_end || in_start>in_end ) return NULL;

        TreeNode* root=new TreeNode(postorder[pos_end]);

        int inroot=in_mpp[root->val];
        int nums_left=inroot-in_start;

        root->left=build_tree(inorder,in_start,inroot-1,postorder,pos_start,pos_start+nums_left-1,in_mpp);

        root->right=build_tree(inorder,inroot+1,in_end,postorder,pos_start+nums_left,pos_end-1,in_mpp);

        return root;
    }

    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) 
    {
        map<int,int> in_mpp;
        for(int i=0;i<inorder.size();i++)
        {
            in_mpp[inorder[i]]=i;
        }   
        TreeNode* root=build_tree(inorder,0,inorder.size()-1,postorder,0,postorder.size()-1,in_mpp);
        
        return root; 
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
