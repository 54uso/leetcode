### Problem
<p>Given an array of numbers <code>nums</code>, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>  <code>[1,2,1,3,2,5]</code>
<strong>Output:</strong> <code>[3,5]</code></pre>

<p><b>Note</b>:</p>

<ol>
	<li>The order of the result is not important. So in the above example, <code>[5, 3]</code> is also correct.</li>
	<li>Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?</li>
</ol>

### Code
```cpp
class Solution {
public:
    int yh(vector<int>& nums, long val, long& low, long& up) {
        int cnt = 0;
        for (vector<int>::iterator it = nums.begin(); it != nums.end(); ++it) {
            if (*it == val) {
                cnt++;
            } else if (*it > val) {
                up ^= *it;
            } else {
                low ^= *it;
            }
        }
        return cnt;
    }
    vector<int> singleNumber(vector<int>& nums) {
        vector<int> vec;
        long l = 1 << 31, r = (1 << 30) - 1 + (1 << 30);
        while (l < r) {
            long mid = (l + r) / 2;
            long low = 0, up = 0;
            int cnt = yh(nums, mid, low, up);
            if (cnt == 1) {
                vec.push_back(mid);
                if (low != 0) {
                    vec.push_back(low);
                } else {
                    vec.push_back(up);
                }
                return vec;
            }
            if (low != 0 && up != 0) {
                vec.push_back(low);
                vec.push_back(up);
                return vec;
            }
            if (low == 0) {
                l = mid + 1;
            } else {
                r = mid - 1;
            }
        }
        return vec;
    }
};
```
