#131 - Palindrome Partitioning

### Problem
<p>Given a string <em>s</em>, partition <em>s</em> such that every substring of the partition is a palindrome.</p>

<p>Return all possible palindrome partitioning of <em>s</em>.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;&quot;aab&quot;
<strong>Output:</strong>
[
  [&quot;aa&quot;,&quot;b&quot;],
  [&quot;a&quot;,&quot;a&quot;,&quot;b&quot;]
]
</pre>


### Code
```java
public class Solution {
    public List<List<String>> partition(String s) {
        int ls = s.length();
        List<Integer>[] arr = new LinkedList[ls];
        for (int i = 0; i < ls; ++i) {
            arr[i] = new LinkedList<Integer>();
            arr[i].add(i);
            if (i == 0) {
                continue;
            }
            if (s.charAt(i) == s.charAt(i - 1)) {
                arr[i].add(i - 1);
            }
            for (int j : arr[i - 1]) {
                if (j > 0 && s.charAt(i) == s.charAt(j - 1)) {
                    arr[i].add(j - 1);
                }
            }
        }
        return solve(ls, arr, s);
    }

    private List<List<String>> solve(int end, List<Integer>[] arr, String str) {
        List<List<String>> ret = new LinkedList<List<String>>();
        if (end == 0) {
            ret.add(new LinkedList<String>());
            return ret;
        }
        for (int i : arr[end - 1]) {
            List<List<String>> tmps = solve(i, arr, str);
            String s = str.substring(i, end);
            for (List<String> tmp : tmps) {
                tmp.add(s);
                ret.add(tmp);
            }
        }
        return ret;
    }
}
```
### Link: [https://leetcode.com/problems/palindrome-partitioning/](https://leetcode.com/problems/palindrome-partitioning/)
