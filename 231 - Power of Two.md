# 231 - Power of Two

### Problem
<p>Given an integer, write a function to determine if it is a power of two.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1
<strong>Output:</strong> true 
<strong>Explanation: </strong>2<sup>0</sup>&nbsp;= 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 16
<strong>Output:</strong> true
<strong>Explanation: </strong>2<sup>4</sup>&nbsp;= 16</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> 218
<strong>Output:</strong> false</pre>


### Code
```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if (n <= 0) {
            return false; 
        }
        while (n > 1) {
            if (n % 2 != 0) {
                return false;
            }
            n /= 2;
        } 
        return true;
    }
};
```
### Link: [https://leetcode.com/problems/power-of-two/](https://leetcode.com/problems/power-of-two/)
