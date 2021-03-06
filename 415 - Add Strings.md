# 415 - Add Strings

### Problem
<p>Given two non-negative integers <code>num1</code> and <code>num2</code> represented as string, return the sum of <code>num1</code> and <code>num2</code>.</p>

<p><b>Note:</b>
<ol>
<li>The length of both <code>num1</code> and <code>num2</code> is < 5100.</li>
<li>Both <code>num1</code> and <code>num2</code> contains only digits <code>0-9</code>.</li>
<li>Both <code>num1</code> and <code>num2</code> does not contain any leading zero.</li>
<li>You <b>must not use any built-in BigInteger library</b> or <b>convert the inputs to integer</b> directly.</li>
</ol>
</p>

### Code
```java
import java.math.BigInteger;

public class Solution {
    public String addStrings(String num1, String num2) {
        return new BigInteger(num1).add(new BigInteger(num2)).toString();
    }
}
```
### Link: [https://leetcode.com/problems/add-strings/](https://leetcode.com/problems/add-strings/)
