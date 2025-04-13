## Boundary Traversal (c++)

Given a root of Binary Tree, perform the boundary traversal of the tree. 

The boundary traversal is the process of visiting the boundary nodes of the binary tree in the anticlockwise direction, starting from the root.

## Example
Input : root = [1, 2, 3, 4, 5, 6, 7, null, null, 8, 9]

Output : [1, 2, 4, 8, 9, 6, 7, 3]

Explanation :

![image](https://github.com/user-attachments/assets/bc034dc1-02bf-450e-83b9-a47ad82b0729)

## PROGRAM:(Main.cpp)
```
class Solution{
public:
    bool isLeaf(TreeNode* node) 
    {
        return (node->left == NULL && node->right == NULL);
    }
    void addleft(TreeNode* root,vector<int> &res)
    {
        TreeNode* node=root->left;
        while(node)
        {
            if(!isLeaf(node)) res.push_back(node->data);
            if(node->left) node=node->left;
            else node=node->right;
        }
    }
    void addright(TreeNode* root,vector<int> &res)
    {
        TreeNode* node=root->right;
        vector<int> temp;
        while(node)
        {
            if(!isLeaf(node)) temp.push_back(node->data);
            if(node->right) node=node->right;
            else node=node->left;
        }
        for(int i=temp.size()-1;i>=0;i--)
        {
            res.push_back(temp[i]);
        }
    }
    void addleaves(TreeNode* root,vector<int> &res)
    {
        if(root==NULL) return;
        if(isLeaf(root)) 
        {
            res.push_back(root->data);
            return;
        }

        addleaves(root->left,res);
        addleaves(root->right,res);
    }
    vector <int> boundary(TreeNode* root)
    {
    	vector<int> res;
        if(root==NULL) return res;
        if(!isLeaf(root)) res.push_back(root->data);
        addleft(root,res);
        addleaves(root,res);
        addright(root,res);
        return res;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
