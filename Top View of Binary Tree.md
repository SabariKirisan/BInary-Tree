## Top View of Binary Tree (c++)

You are given a binary tree, and your task is to return its top view. The top view of a binary tree is the set of nodes visible when the tree is viewed from the top.

Note: 

Return the nodes from the leftmost node to the rightmost node.

If two nodes are at the same position (horizontal distance) and are outside the shadow of the tree, consider the leftmost node only. 

## Example
Input: root[] = [10, 20, 30, 40, 60, 90, 100]

![image](https://github.com/user-attachments/assets/02ef70dd-579b-464e-9520-55a99c284a73)

Output: [40, 20, 10, 30, 100]

Explanation: The root 10 is visible.

On the left, 40 is the leftmost node and visible, followed by 20.

On the right, 30 and 100 are visible. Thus, the top view is 40 20 10 30 100.

## PROGRAM:(Main.cpp)
```
class Solution {
  public:
    vector<int> topView(Node *root) 
    {
        vector<int> ans;
        if(root==NULL) return ans;
        
        map<int,int> mpp;
        queue<pair<Node*,int>> q;
        q.push({root,0});
        while(!q.empty())
        {
            auto it=q.front();
            q.pop();
            Node* node=it.first;
            int line=it.second;
            
            if(mpp.find(line)==mpp.end()) mpp[line]=node->data;
            
            if(node->left !=NULL) 
            {
                q.push({node->left,line-1});
            }
            if(node->right !=NULL)
            {
                q.push({node->right,line+1});
            }
        }
        for(auto it:mpp)
        {
            ans.push_back(it.second);
        }
        return ans;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
