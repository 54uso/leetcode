### Problem
<p>Given a <strong>non-empty</strong>&nbsp;array of integers, every element appears <em>twice</em> except for one. Find that single one.</p>

<p><strong>Note:</strong></p>

<p>Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,2,1]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [4,1,2,1,2]
<strong>Output:</strong> 4
</pre>


### Code
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int ret = 0;
        for (vector<int>::iterator it = nums.begin(); it != nums.end(); it++) {
            ret ^= *it;
        }
        return ret;
    }
};
```
