# 205 - Isomorphic Strings

### Problem
<p>Given two strings <b><i>s</i></b> and <b><i>t</i></b>, determine if they are isomorphic.</p>

<p>Two strings are isomorphic if the characters in <b><i>s</i></b> can be replaced to get <b><i>t</i></b>.</p>

<p>All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> <b><i>s</i></b> = <code>&quot;egg&quot;, </code><b><i>t = </i></b><code>&quot;add&quot;</code>
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> <b><i>s</i></b> = <code>&quot;foo&quot;, </code><b><i>t = </i></b><code>&quot;bar&quot;</code>
<strong>Output:</strong> false</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> <b><i>s</i></b> = <code>&quot;paper&quot;, </code><b><i>t = </i></b><code>&quot;title&quot;</code>
<strong>Output:</strong> true</pre>

<p><b>Note:</b><br />
You may assume both <b><i>s&nbsp;</i></b>and <b><i>t&nbsp;</i></b>have the same length.</p>


### Code
```java
public class Solution {
    public boolean isIsomorphic(String s, String t) {
        return check(s, t) && check(t, s);
    }
    
    private boolean check(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        Map<Character, Character> map = new HashMap<Character, Character>();
        for (int i = 0; i < s.length(); ++i) {
            char ch = s.charAt(i);
            if (map.get(ch) == null) {
                map.put(ch, t.charAt(i));
            }
            if (map.get(ch) != t.charAt(i)) {
                return false;
            }
        }
        return true;
    }
}
```
### Link: [https://leetcode.com/problems/isomorphic-strings/](https://leetcode.com/problems/isomorphic-strings/)
