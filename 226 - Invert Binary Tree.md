### Problem
<p>Invert a binary tree.</p>

<p><strong>Example:</strong></p>

<p>Input:</p>

<pre>
     4
   /   \
  2     7
 / \   / \
1   3 6   9</pre>

<p>Output:</p>

<pre>
     4
   /   \
  7     2
 / \   / \
9   6 3   1</pre>

<p><strong>Trivia:</strong><br />
This problem was inspired by <a href="https://twitter.com/mxcl/status/608682016205344768" target="_blank">this original tweet</a> by <a href="https://twitter.com/mxcl" target="_blank">Max Howell</a>:</p>

<blockquote>Google: 90% of our engineers use the software you wrote (Homebrew), but you can&rsquo;t invert a binary tree on a whiteboard so f*** off.</blockquote>


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
    TreeNode* invertTree(TreeNode* root) {
        if (root != NULL) {
            TreeNode* tmp = root->left;
            root->left = invertTree(root->right);
            root->right = invertTree(tmp);
        }
        return root;
    }
};
```
