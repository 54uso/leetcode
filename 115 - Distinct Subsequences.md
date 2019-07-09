# 115 - Distinct Subsequences

### Problem
<p>Given a string <strong>S</strong> and a string <strong>T</strong>, count the number of distinct subsequences of <strong>S</strong> which equals <strong>T</strong>.</p>

<p>A subsequence of a string is a new string which is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (ie, <code>&quot;ACE&quot;</code> is a subsequence of <code>&quot;ABCDE&quot;</code> while <code>&quot;AEC&quot;</code> is not).</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>S = <code>&quot;rabbbit&quot;</code>, T = <code>&quot;rabbit&quot;
<strong>Output:</strong>&nbsp;3
</code><strong>Explanation:
</strong>
As shown below, there are 3 ways you can generate &quot;rabbit&quot; from S.
(The caret symbol ^ means the chosen letters)

<code>rabbbit</code>
^^^^ ^^
<code>rabbbit</code>
^^ ^^^^
<code>rabbbit</code>
^^^ ^^^
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>S = <code>&quot;babgbag&quot;</code>, T = <code>&quot;bag&quot;
<strong>Output:</strong>&nbsp;5
</code><strong>Explanation:
</strong>
As shown below, there are 5 ways you can generate &quot;bag&quot; from S.
(The caret symbol ^ means the chosen letters)

<code>babgbag</code>
^^ ^
<code>babgbag</code>
^^    ^
<code>babgbag</code>
^    ^^
<code>babgbag</code>
  ^  ^^
<code>babgbag</code>
    ^^^
</pre>


### Code
```java
public class Solution {
    public int numDistinct(String s, String t) {
        int ls = s.length();
        int lt = t.length();
        int dp[][] = new int[lt + 1][ls + 1];
        for (int i = 0; i <= ls; ++i) {
            dp[0][i] = 1;
        }
        for (int i = 1; i <= lt; ++i) {
            for (int j = 1; j <= ls; ++j) {
                dp[i][j] += dp[i][j - 1];
                dp[i][j] += t.charAt(i - 1) == s.charAt(j - 1) ? dp[i - 1][j - 1] : 0;
            }
        }
        return dp[lt][ls];
    }
}
```
### Link: [https://leetcode.com/problems/distinct-subsequences/](https://leetcode.com/problems/distinct-subsequences/)
