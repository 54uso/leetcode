### Problem
<p>Given a binary tree, return the <em>inorder</em> traversal of its nodes&#39; values.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,null,2,3]
   1
    \
     2
    /
   3

<strong>Output:</strong> [1,3,2]</pre>

<p><strong>Follow up:</strong> Recursive solution is trivial, could you do it iteratively?</p>


### Code
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    void dfs(TreeNode* cur, vector<int>& vec) {
        if (cur == NULL) {
            return;
        } 
        dfs(cur->left, vec);
        vec.push_back(cur->val);
        dfs(cur->right, vec);
    }
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> vec;
        dfs(root, vec);
        return vec;
    }
};
```
