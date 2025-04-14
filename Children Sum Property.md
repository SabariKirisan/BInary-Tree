##  Children Sum Property (c++)

Given a binary tree of nodes 'N', you need to modify the value of its nodes, such that the tree holds the Children sum property.

A binary tree is said to follow the children sum property if, for every node of that tree, the value of that node is equal to the sum of the value(s) of all of its children nodes( left child and the right child).

Note :
 1. You can only increment the value of the nodes, in other words, the modified value must be at least equal to the original value of that node.

 2. You can not change the structure of the original binary tree.

 3. A binary tree is a tree in which each node has at most two children.      

 4. You can assume the value can be 0 for a NULL node and there can also be an empty tree.

## Example
Input:

![image](https://github.com/user-attachments/assets/65688c1d-b702-477c-8b7e-e9f78318de0d)

Output: 

![image](https://github.com/user-attachments/assets/6dfc5a5d-a722-4ef7-91c9-6a66490aff77)

## PROGRAM:(Main.cpp)
```
void changeTree(BinaryTreeNode < int > * root) 
{
    if(root==NULL) return;
    int child=0;
    if(root->left) child+=root->left->data;
    if(root->right) child+=root->right->data;

    if(child>=root->data) root->data=child;
    else
    {
        if(root->left) root->left->data=root->data;
        else if(root->right) root->right->data=root->data;
    }
    changeTree(root->left);
    changeTree(root->right);

    int tot=0;
    if(root->left) tot+=root->left->data;
    if(root->right) tot+=root->right->data;
    if(root->left || root->right) root->data=tot; 
}  
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(H) ~ O(N)
