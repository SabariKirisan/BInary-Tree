## Bottom View Of Binary Tree (c++)

You are given a 'Binary Tree'.

Return the bottom view of the binary tree.

## Example
![image](https://github.com/user-attachments/assets/02045f77-786c-4ba7-ba4f-acb463487373)

Output: 4 2 6 3 7

## PROGRAM:(Main.cpp)
```
#include<bits/stdc++.h>
using namespace std;
vector<int> bottomView(TreeNode<int> * root)
{
    vector<int> ans;
    if(root==NULL) return ans;

    map<int,int> mpp;
    queue<pair<TreeNode<int>*,int>> q;
    q.push({root,0});
    while(!q.empty())
    {
        auto p=q.front();
        q.pop();
        TreeNode<int>* node=p.first;
        int line=p.second;
        mpp[line]=node->data;

        if(node->left!=NULL)
        {
            q.push({node->left,line-1});
        }
        if(node->right!=NULL)
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
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
