#279 - Perfect Squares

### Problem
<p>Given a positive integer <i>n</i>, find the least number of perfect square numbers (for example, <code>1, 4, 9, 16, ...</code>) which sum to <i>n</i>.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> <i>n</i> = <code>12</code>
<b>Output:</b> 3 
<strong>Explanation: </strong><code>12 = 4 + 4 + 4.</code></pre>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> <i>n</i> = <code>13</code>
<b>Output:</b> 2
<strong>Explanation: </strong><code>13 = 4 + 9.</code></pre>

### Code
```java
public class Solution {
    
    public int numSquares(int n) {
        int t = (int) Math.sqrt(n);
        int[] dp = new int[n + 1];
        for (int i = 1; i <= n; ++i) {
            dp[i] = Integer.MAX_VALUE;
        }
        for (int i = 1; i <= t; ++i) {
            int m = i * i;
            for (int j = 1; j <= n; ++j) {
                if (j >= m && dp[j] > dp[j - m] + 1) {
                    dp[j] = dp[j - m] + 1;
                }
            }
        }
        return dp[n];
    }
    
}
```
### Link: [https://leetcode.com/problems/perfect-squares/](https://leetcode.com/problems/perfect-squares/)
