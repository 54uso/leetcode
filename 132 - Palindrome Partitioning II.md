# 132 - Palindrome Partitioning II

### Problem
<p>Given a string <em>s</em>, partition <em>s</em> such that every substring of the partition is a palindrome.</p>

<p>Return the minimum cuts needed for a palindrome partitioning of <em>s</em>.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;&quot;aab&quot;
<strong>Output:</strong> 1
<strong>Explanation:</strong> The palindrome partitioning [&quot;aa&quot;,&quot;b&quot;] could be produced using 1 cut.
</pre>


### Code
```java
public class Solution {

    public int minCut(String s) {
        int ls = s.length();
        int[] ans = new int[ls];
        List<Integer> arr = new LinkedList();
        for (int i = 0; i < ls; ++i) {
            arr.add(0, i);
            if (i == 0) {
                ans[i] = 0;
                continue;
            }
            ans[i] = ans[i - 1] + 1;
            List<Integer> tmp = new LinkedList<Integer>();
            tmp.add(i);
            for (int a : arr) {
                if (a != 0) {
                    if (s.charAt(a - 1) == s.charAt(i)) {
                        tmp.add(a - 1);
                        if (a - 1 == 0) {
                            ans[i] = 0;
                        } else {
                            if (ans[a - 2] + 1 < ans[i]) {
                                ans[i] = ans[a - 2] + 1;
                            }
                        }
                    }
                }
            }
            arr = tmp;
        }
        return ans[ls - 1];
    }
    
}
```
### Link: [https://leetcode.com/problems/palindrome-partitioning-ii/](https://leetcode.com/problems/palindrome-partitioning-ii/)
