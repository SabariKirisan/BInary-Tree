## Root Equals Sum of Children (c++)

You are given the root of a binary tree that consists of exactly 3 nodes: the root, its left child, and its right child.

Return true if the value of the root is equal to the sum of the values of its two children, or false otherwise.

## Example
![image](https://github.com/user-attachments/assets/71fcd25d-303d-4f9e-bc5f-7e105396cbde)

Input: root = [10,4,6]

Output: true

Explanation: The values of the root, its left child, and its right child are 10, 4, and 6, respectively.
10 is equal to 4 + 6, so we return true.
## PROGRAM:(Main.cpp)
```
class Solution {
public:
    bool checkTree(TreeNode* root) 
    {
        int sum=0;
        sum=root->left->val+root->right->val;
        if(sum==root->val) return true;
        return false;   
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(1)
