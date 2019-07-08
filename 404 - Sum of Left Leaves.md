### Problem
<p>Find the sum of all left leaves in a given binary tree.</p>

<p><b>Example:</b>
<pre>
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values <b>9</b> and <b>15</b> respectively. Return <b>24</b>.
</pre>
</p>

### Code
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public int sumOfLeftLeaves(TreeNode root) {
        if (root == null) {
            return 0;
        }
        root.val = 0;
        return sum(root);
    }
    
    public int sum(TreeNode root) {
        if (root.left == null && root.right == null) {
            return root.val;
        }
        int t = 0;
        if (root.left != null) {
            t += sum(root.left);
        }
        if (root.right != null) {
            root.right.val = 0;
            t += sum(root.right);
        }
        return t;
    }
}
```
