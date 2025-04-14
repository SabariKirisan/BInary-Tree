## Maximum Width of Binary Tree (c++)

Given the root of a binary tree, return the maximum width of the given tree.

The maximum width of a tree is the maximum width among all levels.

The width of one level is defined as the length between the end-nodes (the leftmost and rightmost non-null nodes), where the null nodes between the end-nodes that would be present in a complete binary tree extending down to that level are also counted into the length calculation.

It is guaranteed that the answer will in the range of a 32-bit signed integer.

## Example
![image](https://github.com/user-attachments/assets/417f0d65-3306-4267-b854-12d638a2b2f5)

Input: root = [1,3,2,5,3,null,9]

Output: 4

Explanation: The maximum width exists in the third level with length 4 (5,3,null,9).
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) 
    {
        if(root==NULL) return 0;
        unsigned long long ans=0;
        queue<pair<TreeNode*,unsigned long long>> q;
        q.push({root,0});
        while(!q.empty())
        {
            int size=q.size();
            unsigned long long first,last;
            unsigned long long minn=q.front().second;
            for(int i=0;i<size;i++)
            {
                unsigned long long cur_id=q.front().second-minn;
                TreeNode* node=q.front().first;
                q.pop();
                if(i==0) first=cur_id;
                if(i==size-1) last=cur_id;
                if(node->left) 
                {
                    q.push({node->left,cur_id*2+1});
                }
                if(node->right)
                {
                    q.push({node->right,cur_id*2+2});
                }
            }
            ans=max(ans,last-first+1);
        }   
        return ans;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
