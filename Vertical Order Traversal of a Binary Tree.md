## Vertical Order Traversal of a Binary Tree (c++)

Given the root of a binary tree, calculate the vertical order traversal of the binary tree.

For each node at position (row, col), its left and right children will be at positions (row + 1, col - 1) and (row + 1, col + 1) respectively. The root of the tree is at (0, 0).

The vertical order traversal of a binary tree is a list of top-to-bottom orderings for each column index starting from the leftmost column and ending on the rightmost column. There may be multiple nodes in the same row and same column. In such a case, sort these nodes by their values.

Return the vertical order traversal of the binary tree.

## Example
![image](https://github.com/user-attachments/assets/5b3baa47-e30b-4650-a88e-3f37b5f3b098)

Input: root = [3,9,20,null,null,15,7]

Output: [[9],[3,15],[20],[7]]

Explanation:

Column -1: Only node 9 is in this column.

Column 0: Nodes 3 and 15 are in this column in that order from top to bottom.

Column 1: Only node 20 is in this column.

Column 2: Only node 7 is in this column.

## PROGRAM:(Main.cpp)
```
class Solution {
public:
    vector<vector<int>> verticalTraversal(TreeNode* root) 
    {
        map<int,map<int,multiset<int>>> nodes;
        queue<pair<TreeNode*,pair<int,int>>> q;
        q.push({root,{0,0}});
        while(!q.empty())
        {
            auto p=q.front();
            q.pop();
            TreeNode* node=p.first;
            int x=p.second.first,y=p.second.second;
            nodes[x][y].insert(node->val);
            if(node->left)
            {
                q.push({node->left,{x-1,y+1}});
            }
            if(node->right)
            {
                q.push({node->right,{x+1,y+1}});
            }
        }
        vector<vector<int>> ans;
        for(auto p:nodes)
        {
            vector<int> col;
            for(auto q:p.second)
            {
                col.insert(col.end(),q.second.begin(),q.second.end());
            }
            ans.push_back(col);
        }
        return ans;
    }
};
```
## Complexity
- Time complexity : O(N log N)

- Space complexity : O(N)
