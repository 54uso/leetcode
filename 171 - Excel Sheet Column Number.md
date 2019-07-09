#171 - Excel Sheet Column Number

### Problem
<p>Given a column title as appear in an Excel sheet, return its corresponding column number.</p>

<p>For example:</p>

<pre>
    A -&gt; 1
    B -&gt; 2
    C -&gt; 3
    ...
    Z -&gt; 26
    AA -&gt; 27
    AB -&gt; 28 
    ...
</pre>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> &quot;A&quot;
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>&quot;AB&quot;
<strong>Output:</strong> 28
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>&quot;ZY&quot;
<strong>Output:</strong> 701
</pre>

### Code
```cpp
class Solution {
public:
    int titleToNumber(string s) {
        int ret = 0, size = s.size();
        for (int i = 0; i < size; ++i) {
            ret = ret * 26 + s[i] - 'A' + 1;
        }
        return ret;
    }
};
```
### Link: [https://leetcode.com/problems/excel-sheet-column-number/](https://leetcode.com/problems/excel-sheet-column-number/)
