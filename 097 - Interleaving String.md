### Problem
<p>Given <em>s1</em>, <em>s2</em>, <em>s3</em>, find whether <em>s3</em> is formed by the interleaving of <em>s1</em> and <em>s2</em>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> s1 = &quot;aabcc&quot;, s2 = &quot;dbbca&quot;, <em>s3</em> = &quot;aadbbcbcac&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> s1 = &quot;aabcc&quot;, s2 = &quot;dbbca&quot;, <em>s3</em> = &quot;aadbbbaccc&quot;
<strong>Output:</strong> false
</pre>


### Code
```java
public class Solution {
    public boolean isInterleave(String s1, String s2, String s3) {
        int l1 = s1.length();
        int l2 = s2.length();
        int l3 = s3.length();
        if (l1 == 0 && l2 == 0 && l3 == 0) {
            return true;
        }
        if (l1 + l2 != l3) {
            return false;
        }
        if (l1 == 0) {
            return s3.compareTo(s2) == 0;
        }
        boolean[][] dp = new boolean[l3 + 1][l1 + 1];
        dp[0][0] = true;
        for (int i = 1; i <= l3; ++i) {
            for (int j = 0; j <= l1 && j <= i; ++j) {
                if ((j > 0 && dp[i - 1][j - 1] && s3.charAt(i - 1) == s1.charAt(j - 1))
                    || (i - j >= 1 && i - j <= l2 && dp[i - 1][j] && s3.charAt(i - 1) == s2.charAt(i - j - 1))) {
                    //System.out.println(i + " " + j);
                    dp[i][j] = true;
                }
            }
        }
        return dp[l3][l1];
    }
}
```
