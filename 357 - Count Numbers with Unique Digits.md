#357 - Count Numbers with Unique Digits

### Problem
<p>Given a <b>non-negative</b> integer n, count all numbers with unique digits, x, where 0 &le; x &lt; 10<sup>n</sup>.</p>

<div>
<p><strong>Example:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">2</span>
<strong>Output: </strong><span id="example-output-1">91 
<strong>Explanation: </strong></span>The answer should be the total numbers in the range of 0 &le; x &lt; 100, 
&nbsp;            excluding <code>11,22,33,44,55,66,77,88,99</code>
</pre>
</div>

### Code
```java
public class Solution {
    public int countNumbersWithUniqueDigits(int n) {
        if (n == 0) {
            return 1;
        }
        if (n == 1) {
            return 10;
        }
        int cur = 10, mul = 9;
        for (int i = 2, j = 9; i <= n; --j, ++i) {
            mul = mul * j;
            cur += mul;
        }
        return cur;
    }
}
```
### Link: [https://leetcode.com/problems/count-numbers-with-unique-digits/](https://leetcode.com/problems/count-numbers-with-unique-digits/)
