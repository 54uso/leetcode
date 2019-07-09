# 137 - Single Number II

### Problem
<p>Given a <strong>non-empty</strong>&nbsp;array of integers, every element appears <em>three</em> times except for one, which appears exactly once. Find that single one.</p>

<p><strong>Note:</strong></p>

<p>Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,2,3,2]
<strong>Output:</strong> 3
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [0,1,0,1,0,1,99]
<strong>Output:</strong> 99</pre>


### Code
```cpp

class Solution {
public:
    long yh(long a, long b) {
        long j = 1, ret = 0;
        while (a != 0 || b != 0) {
            ret = (a + b) % 3 * j + ret;
            j *= 3;
            a /= 3;
            b /= 3;
        }
        return ret;
    }
    int singleNumber(vector<int>& nums) {
        long ret = 0, retf = 0;
        for (vector<int>::iterator it = nums.begin(); it != nums.end(); it++) {
            if (*it < 0) {
                retf = yh(retf, -*it);
            } else {
                ret = yh(ret, *it);
            }
        }
        return ret - retf;
    }
};
```
### Link: [https://leetcode.com/problems/single-number-ii/](https://leetcode.com/problems/single-number-ii/)
