# 258 - Add Digits

### Problem
<p>Given a non-negative integer <code>num</code>, repeatedly add all its digits until the result has only one digit.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> <code>38</code>
<strong>Output:</strong> 2 
<strong>Explanation: </strong>The process is like: <code>3 + 8 = 11</code>, <code>1 + 1 = 2</code>. 
&nbsp;            Since <code>2</code> has only one digit, return it.
</pre>

<p><b>Follow up:</b><br />
Could you do it without any loop/recursion in O(1) runtime?</p>

### Code
```cpp
class Solution {
public:
    int addDigits(int num) {
        int m = num;
        while (m >= 10) {
            int t = 0;
            while (m >= 10) {
                t += m % 10;
                m /= 10;
            }
            m += t;
        }
        return m;
    }
};
```
### Link: [https://leetcode.com/problems/add-digits/](https://leetcode.com/problems/add-digits/)
