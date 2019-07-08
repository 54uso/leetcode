### Problem
<p>Given an integer, write a function to determine if it is a power of three.</p>

<p><b>Example 1:</b></p>

<pre>
<strong>Input:</strong> 27
<strong>Output:</strong> true
</pre>

<p><b>Example 2:</b></p>

<pre>
<strong>Input:</strong> 0
<strong>Output:</strong> false</pre>

<p><b>Example 3:</b></p>

<pre>
<strong>Input:</strong> 9
<strong>Output:</strong> true</pre>

<p><b>Example 4:</b></p>

<pre>
<strong>Input:</strong> 45
<strong>Output:</strong> false</pre>

<p><b>Follow up:</b><br />
Could you do it without using any loop / recursion?</p>

### Code
```cpp
class Solution {
public:
    int logN(long a, long b) {
        return log(b * 1.0) / log(a * 1.0);
    }
    bool isPowerOfThree(int n) {
        if (n == 0) {
            return 0;
        }
        int a = logN(3, n);
        return pow(3, a) == n || pow(3, a - 1) == n || pow(3, a + 1) == n;
    }
};
```
