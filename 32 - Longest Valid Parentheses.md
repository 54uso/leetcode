#32 - Longest Valid Parentheses

### Problem
<p>Given a string containing just the characters <code>&#39;(&#39;</code> and <code>&#39;)&#39;</code>, find the length of the longest valid (well-formed) parentheses substring.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> &quot;(()&quot;
<strong>Output:</strong> 2
<strong>Explanation:</strong> The longest valid parentheses substring is <code>&quot;()&quot;</code>
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> &quot;<code>)()())</code>&quot;
<strong>Output:</strong> 4
<strong>Explanation:</strong> The longest valid parentheses substring is <code>&quot;()()&quot;</code>
</pre>


### Code
```java
public class Solution {
    public int longestValidParentheses(String s) {
        int len = s.length();
        if (len < 2) {
            return 0;
        }
        int ret = 0;
        int pre[] = new int[len];
        pre[0] = -1;
        for (int i = 1; i < len; ++i) {
            pre[i] = -1;
            if (s.charAt(i) == '(') {
                continue;
            }
            if (s.charAt(i - 1) == '(') {
                pre[i] = i - 1;
            } else {
                if (pre[i - 1] > 0 && s.charAt(pre[i - 1] - 1) == '(') {
                    pre[i] = pre[i - 1] - 1;
                }
            }
            if (pre[i] > 0 && pre[pre[i] - 1] != -1) {
                pre[i] = pre[pre[i] - 1];
            }
            if (pre[i] != -1 && i - pre[i] + 1 > ret) {
                ret = i - pre[i] + 1;
            }
        }
        return ret;
    }
}
```
### Link: [https://leetcode.com/problems/longest-valid-parentheses/](https://leetcode.com/problems/longest-valid-parentheses/)
