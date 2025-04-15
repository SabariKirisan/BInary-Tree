## Flatten Binary Tree to Linked List(Recursion) (c++)

Given the root of a binary tree, flatten the tree into a "linked list":

The "linked list" should use the same TreeNode class where the right child pointer points to the next node in the list and the left child pointer is always null.

The "linked list" should be in the same order as a pre-order traversal of the binary tree.

## Example
![image](https://github.com/user-attachments/assets/35f156ed-054f-4d68-b554-87904dae22f3)

Input: root = [1,2,5,3,4,null,6]

Output: [1,null,2,null,3,null,4,null,5,null,6]
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    TreeNode* prev=NULL;
    void flatten(TreeNode* root) 
    {
        if(root==NULL) return;

        flatten(root->right);
        flatten(root->left);

        root->right=prev;
        root->left=NULL;
        prev=root;
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
