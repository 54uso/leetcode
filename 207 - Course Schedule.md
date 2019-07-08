### Problem
<p>There are a total of <i>n</i> courses you have to take, labeled from <code>0</code> to <code>n-1</code>.</p>

<p>Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: <code>[0,1]</code></p>

<p>Given the total number of courses and a list of prerequisite <b>pairs</b>, is it possible for you to finish all courses?</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 2, [[1,0]] 
<strong>Output: </strong>true
<strong>Explanation:</strong>&nbsp;There are a total of 2 courses to take. 
&nbsp;            To take course 1 you should have finished course 0. So it is possible.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 2, [[1,0],[0,1]]
<strong>Output: </strong>false
<strong>Explanation:</strong>&nbsp;There are a total of 2 courses to take. 
&nbsp;            To take course 1 you should have finished course 0, and to take course 0 you should
&nbsp;            also have finished course 1. So it is impossible.
</pre>

<p><b>Note:</b></p>

<ol>
	<li>The input prerequisites is a graph represented by <b>a list of edges</b>, not adjacency matrices. Read more about <a href="https://www.khanacademy.org/computing/computer-science/algorithms/graph-representation/a/representing-graphs" target="_blank">how a graph is represented</a>.</li>
	<li>You may assume that there are no duplicate edges in the input prerequisites.</li>
</ol>


### Code
```java
public class Solution {

    private Node[] nodes;

    private int[] tail;

    private int[] status;

    public boolean canFinish(int numCourses, int[][] prerequisites) {
        int len = prerequisites.length;
        if (len == 0) {
            return true;
        }
        this.tail = new int[numCourses];
        this.nodes = new Node[len + 1];
        for (int i = 1; i <= len; ++i) {
            int[] tmp = prerequisites[i - 1];
            this.nodes[i] = new Node(this.tail[tmp[0]], tmp[1]);
            this.tail[tmp[0]] = i;
        }
        this.status = new int[numCourses];
        for (int i = 0; i < numCourses; ++i) {
            if (this.status[i] == 0 && this.dfs(i)) {
                return false;
            }
        }
        return true;
    }

    private boolean dfs(int index) {
        this.status[index] = 1;
        for (int i = tail[index]; i != 0; i = this.nodes[i].getPre()) {
            int t = this.nodes[i].getChild();
            //System.out.println(index + " " + i + " " + t);
            if (this.status[t] == 1) {
                return true;
            }
            if (this.status[t] == 0 && this.dfs(t)) {
                return true;
            }
        }
        this.status[index] = 2;
        return false;
    }

    private class Node {

        private int pre;

        private int child;

        public Node(int pre, int child) {
            this.pre = pre;
            this.child = child;
        }

        public int getPre() {
            return pre;
        }

        public int getChild() {
            return child;
        }

    }

}
```
