# 313 - Super Ugly Number

### Problem
<p>Write a program to find the <code>n<sup>th</sup></code> super ugly number.</p>

<p>Super ugly numbers are positive numbers whose all prime factors are in the given prime list <code>primes</code> of size <code>k</code>.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b> n = 12, <code>primes</code> = <code>[2,7,13,19]</code>
<b>Output:</b> 32 
<strong>Explanation: </strong><code>[1,2,4,7,8,13,14,16,19,26,28,32] </code>is the sequence of the first 12 
             super ugly numbers given <code>primes</code> = <code>[2,7,13,19]</code> of size 4.</pre>

<p><b>Note:</b></p>

<ul>
	<li><code>1</code> is a super ugly number for any given <code>primes</code>.</li>
	<li>The given numbers in <code>primes</code> are in ascending order.</li>
	<li>0 &lt; <code>k</code> &le; 100, 0 &lt; <code>n</code> &le; 10<sup>6</sup>, 0 &lt; <code>primes[i]</code> &lt; 1000.</li>
	<li>The n<sup>th</sup> super ugly number is guaranteed to fit in a 32-bit signed integer.</li>
</ul>


### Code
```java
public class Solution {

    public int nthSuperUglyNumber(int n, int[] primes) {
        int len = primes.length;
        int[] dp = new int[n];
        dp[0] = 1;
        Set<Integer> set = new HashSet<Integer>();
        set.add(1);
        PriorityQueue<Node> queue = new PriorityQueue<Node>(new Comparator<Node>() {
            @Override
            public int compare(Node o1, Node o2) {
                return o1.getVal() - o2.getVal();
            }
        });
        for (int i = 0; i < len; ++i) {
            queue.add(new Node(primes[i], 0, primes[i]));
        }
        for (int i  = 1; i < n; ++i) {
            Node node = queue.poll();
            //System.out.println(node.getVal());
            dp[i] = node.getVal();
            int index = node.getIndex() + 1;
            int val = dp[index] * node.getBase();
            while (set.contains(val)) {
                index = index + 1;
                val = dp[index] * node.getBase();
            }
            set.add(val);
            queue.add(new Node(val, index, node.getBase()));
        }
        return dp[n - 1];
    }

    private class Node {

        private int val;

        private int index;

        private int base;

        public Node(int val, int index, int base) {
            this.val = val;
            this.index = index;
            this.base = base;
        }

        public int getVal() {
            return val;
        }

        public int getIndex() {
            return index;
        }

        public int getBase() {
            return base;
        }
        
    }

}
```
### Link: [https://leetcode.com/problems/super-ugly-number/](https://leetcode.com/problems/super-ugly-number/)
