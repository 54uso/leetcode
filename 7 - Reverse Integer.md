#7 - Reverse Integer

### Problem
<p>Given a 32-bit signed integer, reverse digits of an integer.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 123
<strong>Output:</strong> 321
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> -123
<strong>Output:</strong> -321
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> 120
<strong>Output:</strong> 21
</pre>

<p><strong>Note:</strong><br />
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.</p>


### Code
```java
public class Solution {
    public int reverse(int x) {
        long ret = 0, flag = 1, xx = x;
        if (xx < 0) {
            xx = -xx;
            flag = -1;
        }
        while (xx != 0) {
            int t = (int) (ret * 10 + xx % -10);
            if (t / 10 < ret) {
                return 0;
            }
            ret = t;
            xx = xx / 10;
        }
        return (int) (ret * flag);
    }
}
```
### Link: [https://leetcode.com/problems/reverse-integer/](https://leetcode.com/problems/reverse-integer/)
