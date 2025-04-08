## Binary Tree Representation (Queue) (c++)

You are given an array nodes. It contains 7 integers, which represents the value of nodes of the binary tree in level order traversal. You are also given a root of the tree which has a value equal to nodes[0].

Your task to construct a binary tree by creating nodes for the remaining 6 nodes.

## Example
Input: nodes = [1 2 3 4 5 6 7]

Output: [1 2 3 4 5 6 7]

Explanation: The 7 node binary tree is represented above.

## PROGRAM:(Main.cpp)
```
class Solution{
public:

    void create_tree(node* root0, vector<int> &vec)
    {
        
        if (vec.empty() || root0 == nullptr) return;

        queue<node*> q;
        q.push(root0);
        int i = 1;

        while (!q.empty() && i < vec.size()) 
        {
            node* current = q.front();
            q.pop();

           
            if (i < vec.size()) 
            {
                current->left = newNode(vec[i++]);
                q.push(current->left);
            }

            if (i < vec.size()) 
            {
                current->right = newNode(vec[i++]);
                q.push(current->right);
            }
        }
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)

