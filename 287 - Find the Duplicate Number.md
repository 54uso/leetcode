# 287 - Find the Duplicate Number

### Problem
<p>Given an array <i>nums</i> containing <i>n</i> + 1 integers where each integer is between 1 and <i>n</i> (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> <code>[1,3,4,2,2]</code>
<b>Output:</b> 2
</pre>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> [3,1,3,4,2]
<b>Output:</b> 3</pre>

<p><b>Note:</b></p>

<ol>
	<li>You <b>must not</b> modify the array (assume the array is read only).</li>
	<li>You must use only constant, <i>O</i>(1) extra space.</li>
	<li>Your runtime complexity should be less than <em>O</em>(<em>n</em><sup>2</sup>).</li>
	<li>There is only one duplicate number in the array, but it could be repeated more than once.</li>
</ol>


### Code
```cpp
class Solution {
public:
    int cmp(vector<int>& nums, int val, int& low, int& up) {
        int t = 0;
        for (vector<int>::iterator it = nums.begin(); it != nums.end(); ++it) {
            if (*it == val) {
                t++;
            } else if (*it > val) {
                up++;
            } else {
                low++;
            }
        }
        return t;
    }
    
    int findDuplicate(vector<int>& nums) {
        int n = nums.size() - 1;
        int l = 1, r = n;
        while (l < r) {
            int mid = (l + r) / 2, low = 0, up = 0;
            int cnt = cmp(nums, mid, low, up);
            if (cnt > 1) {
                return mid;
            }
            if (low >= mid) {
                r = mid - 1;
            } else {
                l = mid + 1;
            }
        }
        return l;
    }
};
```
### Link: [https://leetcode.com/problems/find-the-duplicate-number/](https://leetcode.com/problems/find-the-duplicate-number/)
