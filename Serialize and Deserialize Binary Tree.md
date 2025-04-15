## Serialize and Deserialize Binary Tree (c++)

Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

Clarification: The input/output format is the same as how LeetCode serializes a binary tree. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.

## Example
![image](https://github.com/user-attachments/assets/b8bdf0a5-db91-404b-bee8-6fc0650fcd00)

Input: root = [1,2,3,null,null,4,5]

Output: [1,2,3,null,null,4,5]
## PROGRAM:(Main.cpp)
```
class Codec {
public:
    string serialize(TreeNode* root) 
    {
        if(!root) return "";

        string s="";
        queue <TreeNode*> q;
        q.push(root);
        while(!q.empty())
        {
            TreeNode* node=q.front();
            q.pop();

            if(node==NULL) s.append("#,");
            else s.append(to_string(node->val)+',');
            if(node!=NULL)
            {
                q.push(node->left);
                q.push(node->right);
            }
        }
        return s;
    }

    // Decodes your encoded data to tree.
    TreeNode* deserialize(string data) 
    {
        if(data.size()==0) return NULL;
        stringstream s(data);
        string str;
        getline(s,str,',');
        TreeNode* root=new TreeNode(stoi(str));
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty())
        {
            TreeNode* node=q.front();
            q.pop();

            getline(s,str,',');
            if(str=="#")
            {
                node->left=NULL;
            } 
            else
            {
                TreeNode* leftnode=new TreeNode(stoi(str));
                node->left=leftnode;
                q.push(leftnode);
            }
            getline(s,str,',');
            if(str=="#")
            {
                node->right=NULL;
            }
            else
            {
                TreeNode* rightnode=new TreeNode(stoi(str));
                node->right=rightnode;
                q.push(rightnode);
            }
        }  
        return root; 
    }
};
```
## Complexity
- Time complexity : O(N)

- Space complexity : O(N)
