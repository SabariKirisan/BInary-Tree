## Binary Tree Level Order Traversal (c++)

Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

## Example
Input: root = [1,2,3,4,5,null,8,null,null,6,7,9]

Output: [4,2,6,5,7,1,3,9,8]

Explanation:

![image](https://github.com/user-attachments/assets/222ebd7d-520f-47d2-b1a0-0d4cc0a0d292)

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) 
    {
        vector<vector<int>> ans;
        if(root==NULL) return ans;
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty())
        {
            int size=q.size();
            vector<int> level;
            for(int i=0;i<size;i++)
            {
                TreeNode* node= q.front();
                q.pop();
                if(node->left!=NULL) q.push(node->left);
                if(node->right!=NULL) q.push(node->right);
                level.push_back(node->val);
            }
            ans.push_back(level);
        }
        return ans; 
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)

