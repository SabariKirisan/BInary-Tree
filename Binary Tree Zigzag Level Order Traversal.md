## Binary Tree Zigzag Level Order Traversal (c++)

Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).

## Example
![image](https://github.com/user-attachments/assets/a0e9889d-058e-4379-9384-eec171bf7bd7)

Input: root = [3,9,20,null,null,15,7]

Output: [[3],[20,9],[15,7]]
## PROGRAM:(Main.cpp)
```
class Solution 
{
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) 
    {
        vector<vector<int>> result;
        if(root==NULL) return result;

        queue<TreeNode*> q;
        q.push(root);
        bool left_to_right=true;
        while(!q.empty())
        {
            int size=q.size();
            vector<int> row(size);
            for(int i=0;i<size;i++)
            {
                TreeNode* node=q.front();
                q.pop();

                int index=(left_to_right) ? i : size-i-1;
                row[index]=node->val;

                if(node->left) q.push(node->left);
                if(node->right) q.push(node->right);
            }
            left_to_right=!left_to_right;
            result.push_back(row);
        }   
        return result;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
