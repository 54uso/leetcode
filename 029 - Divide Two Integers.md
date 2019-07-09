# 29 - Divide Two Integers

### Problem
<p>Given two integers <code>dividend</code> and <code>divisor</code>, divide two integers without using multiplication, division and mod operator.</p>

<p>Return the quotient after dividing <code>dividend</code> by <code>divisor</code>.</p>

<p>The integer division should truncate toward zero.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> dividend = 10, divisor = 3
<strong>Output:</strong> 3</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> dividend = 7, divisor = -3
<strong>Output:</strong> -2</pre>

<p><strong>Note:</strong></p>

<ul>
	<li>Both dividend and divisor&nbsp;will be&nbsp;32-bit&nbsp;signed integers.</li>
	<li>The divisor will never be 0.</li>
	<li>Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [&minus;2<sup>31</sup>, &nbsp;2<sup>31</sup> &minus; 1]. For the purpose of this problem, assume that your function returns 2<sup>31</sup> &minus; 1 when the division result&nbsp;overflows.</li>
</ul>


### Code
```java
public class Solution {
    public int divide(int dividend, int divisor) {
        int flag = 0;
        long a = dividend;
        long b = divisor;
        if (a < 0) {
            flag++;
            a = -a;
        }
        if (b < 0) {
            flag++;
            b = -b;
        }
        long ret = 0;
        for (int i = 30; i >= 0; --i) {
            while (a >= b << i) {
                a -= b << i;
                ret += 1 << i;
            }
        }
        //return (int)(flag == 1 ? -ret : ret);
        if (flag == 1) {
            ret = -ret;
        }
        if (ret > Integer.MAX_VALUE) {
            ret = Integer.MAX_VALUE;
        }
        return (int) ret;
    }
}
```
### Link: [https://leetcode.com/problems/divide-two-integers/](https://leetcode.com/problems/divide-two-integers/)
