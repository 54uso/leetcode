### Problem
<p>Given a string, find the length of the <b>longest substring</b> without repeating characters.</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">&quot;abcabcbb&quot;</span>
<strong>Output: </strong><span id="example-output-1">3 
<strong>Explanation:</strong></span> The answer is <code>&quot;abc&quot;</code>, with the length of 3. 
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">&quot;bbbbb&quot;</span>
<strong>Output: </strong><span id="example-output-2">1
</span><span id="example-output-1"><strong>Explanation: </strong>T</span>he answer is <code>&quot;b&quot;</code>, with the length of 1.
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-3-1">&quot;pwwkew&quot;</span>
<strong>Output: </strong><span id="example-output-3">3
</span><span id="example-output-1"><strong>Explanation: </strong></span>The answer is <code>&quot;wke&quot;</code>, with the length of 3. 
             Note that the answer must be a <b>substring</b>, <code>&quot;pwke&quot;</code> is a <i>subsequence</i> and not a substring.
</pre>
</div>
</div>
</div>


### Code
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int m[128] = {0};
        int curIndex = 1, ret = 0;
        int startIndex = 0;
        for (string::iterator iter = s.begin(); iter != s.end(); ++iter) {
            startIndex = max(startIndex, m[*iter]);
            int len = curIndex - startIndex;
            if (len > ret) {
                ret = len;
            }
            m[*iter] = curIndex;
            curIndex++;
        }
        return ret;
    }
};
```
