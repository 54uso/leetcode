# 268 - Missing Number

### Problem
<p>Given an array containing <i>n</i> distinct numbers taken from <code>0, 1, 2, ..., n</code>, find the one that is missing from the array.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> [3,0,1]
<b>Output:</b> 2
</pre>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> [9,6,4,2,3,5,7,0,1]
<b>Output:</b> 8
</pre>

<p><b>Note</b>:<br />
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?</p>

### Code
```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int res = 0, i = 0;
        for (vector<int>::iterator it = nums.begin(); it != nums.end(); ++it) {
            res = res ^ i ^ *it;
            i++;
        }
        return res ^ i;
    }
};
```
### Link: [https://leetcode.com/problems/missing-number/](https://leetcode.com/problems/missing-number/)
