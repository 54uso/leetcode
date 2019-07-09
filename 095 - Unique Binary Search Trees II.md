# 95 - Unique Binary Search Trees II

### Problem
<p>Given an integer <em>n</em>, generate all structurally unique <strong>BST&#39;s</strong> (binary search trees) that store values 1 ...&nbsp;<em>n</em>.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 3
<strong>Output:</strong>
[
&nbsp; [1,null,3,2],
&nbsp; [3,2,null,1],
&nbsp; [3,1,null,null,2],
&nbsp; [2,1,3],
&nbsp; [1,null,2,null,3]
]
<strong>Explanation:</strong>
The above output corresponds to the 5 unique BST&#39;s shown below:

   1         3     3      2      1
    \       /     /      / \      \
     3     2     1      1   3      2
    /     /       \                 \
   2     1         2                 3
</pre>


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
    
    public List<TreeNode> generateTrees(int n) {
        if (n == 0) {
            return new LinkedList<TreeNode>();
        }
        return this.createTrees(1, n);
    }
    
    private List<TreeNode> createTrees(int left, int right) {
        List<TreeNode> nodes = new LinkedList<TreeNode>();
        if (left > right) {
            nodes.add(null);
            return nodes;
        }
        
        for (int i = left; i <= right; ++i) {
            List<TreeNode> lefts = this.createTrees(left, i - 1);
            List<TreeNode> rights = this.createTrees(i + 1, right);
            for (TreeNode node1 : lefts) {
                for (TreeNode node2 : rights) {
                    TreeNode node = new TreeNode(i);
                    node.left = node1;
                    node.right = node2;
                    nodes.add(node);
                }
            }
        }
        return nodes;
    }
    
}
```
### Link: [https://leetcode.com/problems/unique-binary-search-trees-ii/](https://leetcode.com/problems/unique-binary-search-trees-ii/)
