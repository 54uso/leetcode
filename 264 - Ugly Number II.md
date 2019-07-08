### Problem
<p>Write a program to find the <code>n</code>-th ugly number.</p>

<p>Ugly numbers are<strong> positive numbers</strong> whose prime factors only include <code>2, 3, 5</code>.&nbsp;</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> n = 10
<strong>Output:</strong> 12
<strong>Explanation: </strong><code>1, 2, 3, 4, 5, 6, 8, 9, 10, 12</code> is the sequence of the first <code>10</code> ugly numbers.</pre>

<p><strong>Note: </strong>&nbsp;</p>

<ol>
	<li><code>1</code> is typically treated as an ugly number.</li>
	<li><code>n</code> <b>does not exceed 1690</b>.</li>
</ol>

### Code
```java
public class Solution {
    
    public int nthUglyNumber(int n) {
        int[] ans = new int[n];
        ans[0] = 1;
        int index2 = 0, index3 = 0, index5 = 0;
        for (int i = 1; i < n; ++i) {
            int t2 = ans[index2] * 2;
            int t3 = ans[index3] * 3;
            int t5 = ans[index5] * 5;
            int t = this.min(t2, t3, t5);
            if (t2 == t) {
                index2++;
            }
            if (t3 == t) {
                index3++;
            }
            if (t5 == t) {
                index5++;
            }
            ans[i] = t;
        }
        return ans[n - 1];
    }
    
    int min(int a, int b, int c) {
        return this.min(a, this.min(b, c));
    }
    
    int min(int a, int b) {
        return a < b ? a : b;
    }
    
}
```
