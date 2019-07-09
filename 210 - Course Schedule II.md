# 210 - Course Schedule II

### Problem
<p>There are a total of <em>n</em> courses you have to take, labeled from <code>0</code> to <code>n-1</code>.</p>

<p>Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: <code>[0,1]</code></p>

<p>Given the total number of courses and a list of prerequisite <strong>pairs</strong>, return the ordering of courses you should take to finish all courses.</p>

<p>There may be multiple correct orders, you just need to return one of them. If it is impossible to finish all courses, return an empty array.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 2, [[1,0]] 
<strong>Output: </strong><code>[0,1]</code>
<strong>Explanation:</strong>&nbsp;There are a total of 2 courses to take. To take course 1 you should have finished   
&nbsp;            course 0. So the correct course order is <code>[0,1] .</code></pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 4, [[1,0],[2,0],[3,1],[3,2]]
<strong>Output: </strong><code>[0,1,2,3] or [0,2,1,3]</code>
<strong>Explanation:</strong>&nbsp;There are a total of 4 courses to take. To take course 3 you should have finished both     
             courses 1 and 2. Both courses 1 and 2 should be taken after you finished course 0. 
&nbsp;            So one correct course order is <code>[0,1,2,3]</code>. Another correct ordering is <code>[0,2,1,3] .</code></pre>

<p><strong>Note:</strong></p>

<ol>
	<li>The input prerequisites is a graph represented by <strong>a list of edges</strong>, not adjacency matrices. Read more about <a href="https://www.khanacademy.org/computing/computer-science/algorithms/graph-representation/a/representing-graphs" target="_blank">how a graph is represented</a>.</li>
	<li>You may assume that there are no duplicate edges in the input prerequisites.</li>
</ol>


### Code
```java
import java.util.Queue;
import java.util.concurrent.LinkedBlockingQueue;

public class Solution {

    public int[] findOrder(int numCourses, int[][] prerequisites) {
        int len = prerequisites.length;
        int[] degree = new int[numCourses];
        int[] tail = new int[numCourses];
        Node[] nodes = new Node[len + 1];
        for (int i = 1; i <= len; ++i) {
            int[] tmp = prerequisites[i - 1];
            nodes[i] = new Node(tail[tmp[1]], tmp[0]);
            tail[tmp[1]] = i;
            degree[tmp[0]]++;
        }
        Queue<Integer> queue = new LinkedBlockingQueue<Integer>();
        for (int i = 0; i < numCourses; ++i) {
            if (degree[i] == 0) {
                queue.add(i);
            }
        }
        int[] ret = new int[numCourses];
        int cnt = 0;
        while (!queue.isEmpty()) {
            int index = queue.remove();
            ret[cnt++] = index;
            for (int i = tail[index]; i != 0; i = nodes[i].getPre()) {
                int t = nodes[i].getChild();
                degree[t]--;
                if (degree[t] == 0) {
                    queue.add(t);
                }
            }
        }
        return cnt == numCourses ? ret : new int[]{};
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
### Link: [https://leetcode.com/problems/course-schedule-ii/](https://leetcode.com/problems/course-schedule-ii/)
