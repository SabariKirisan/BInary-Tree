## Binary Tree Maximum Path Sum (c++)

A path in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence at most once. Note that the path does not need to pass through the root.

The path sum of a path is the sum of the node's values in the path.

Given the root of a binary tree, return the maximum path sum of any non-empty path.

## Example
![image](https://github.com/user-attachments/assets/82bba893-3cec-4f67-abe0-b0849cd2311e)

Input: root = [-10,9,20,null,null,15,7]

Output: 42

Explanation: The optimal path is 15 -> 20 -> 7 with a path sum of 15 + 20 + 7 = 42.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int maxpath(TreeNode* root,int &maxi)
    {
        if(root==NULL) return 0;

        int left=max(0,maxpath(root->left,maxi));
        int right=max(0,maxpath(root->right,maxi));

        maxi=max(maxi,left+right+root->val);

        return root->val+max(left,right);
    }
    int maxPathSum(TreeNode* root) 
    {
        int maxi=INT_MIN;
        maxpath(root,maxi);
        return maxi;   
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
