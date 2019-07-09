#263 - Ugly Number

### Problem
<p>Write a program to check whether a given number is an ugly number.</p>

<p>Ugly numbers are <strong>positive numbers</strong> whose prime factors only include <code>2, 3, 5</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 6
<strong>Output:</strong> true
<strong>Explanation: </strong>6 = 2 &times;&nbsp;3</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 8
<strong>Output:</strong> true
<strong>Explanation: </strong>8 = 2 &times; 2 &times;&nbsp;2
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> 14
<strong>Output:</strong> false 
<strong>Explanation: </strong><code>14</code> is not ugly since it includes another prime factor <code>7</code>.
</pre>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1</code> is typically treated as an ugly number.</li>
	<li>Input is within the 32-bit signed integer range:&nbsp;[&minus;2<sup>31</sup>,&nbsp; 2<sup>31&nbsp;</sup>&minus; 1].</li>
</ol>

### Code
```cpp
class Solution {
    public:
    long logN(long a, long b) {
        return log(b * 1.0) / log(a * 1.0);
    }
    
    long yu(long n, long m) {
        int num = logN(m, n);
        while (num) {
            int a = pow(m, num);
            while (n % a == 0) {
                n /= a;
            }
            num /= 2;
        }
        return n;
    }
    
    bool isUgly(int n) {
        long num = n;
        if (num < 0) {
            return 0;
        }
        num = yu(num, 2);
        if (num == 1) {
            return true;
        }
        num = yu(num, 3);
        if (num == 1) {
            return true;
        }
        return yu(num, 5) == 1;
    }
};
```
### Link: [https://leetcode.com/problems/ugly-number/](https://leetcode.com/problems/ugly-number/)
