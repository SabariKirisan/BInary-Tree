## Path In A Tree (c++)

You are given a binary tree with ‘N’ number of nodes and a node ‘X’. Your task is to print the path from the root node to the given node ‘X’.

A binary tree is a hierarchical data structure in which each node has at most two children.

## Example
![image](https://github.com/user-attachments/assets/08ee6b4b-38fe-4a1b-8ef1-15f6752db654)

Input: Here, for ‘X ’= 7

Output: the output will be 1 3 7
## PROGRAM:(Main.cpp)
```
#include<bits/stdc++.h>
using namespace std;
bool path(TreeNode<int>* root,vector<int> &ans,int x)
{
	if(root==NULL) return false;
	ans.push_back(root->data);
	if(root->data==x) return true;

	if(path(root->left,ans,x)||path(root->right,ans,x))
	return true;

	ans.pop_back();
	return false;
}
vector<int> pathInATree(TreeNode<int> *root, int x)
{
    vector<int> ans;
	if(root==NULL) return ans;

	path(root,ans,x);
	return ans;
}
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
