#238 - Product of Array Except Self

### Problem
<p>Given an array <code>nums</code> of <em>n</em> integers where <em>n</em> &gt; 1, &nbsp;return an array <code>output</code> such that <code>output[i]</code> is equal to the product of all the elements of <code>nums</code> except <code>nums[i]</code>.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b>  <code>[1,2,3,4]</code>
<b>Output:</b> <code>[24,12,8,6]</code>
</pre>

<p><strong>Note: </strong>Please solve it <strong>without division</strong> and in O(<em>n</em>).</p>

<p><strong>Follow up:</strong><br />
Could you solve it with constant space complexity? (The output array <strong>does not</strong> count as extra space for the purpose of space complexity analysis.)</p>


### Code
```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> vec; 
        int size = nums.size(); 
        if (size == 0 || size == 1) {
            return vec;
        }
        int t = 1, a[size], c[size];
        for (int i = 0; i < size; ++i) {
            a[i] = t * nums[i];
            t *= nums[i];
        }
        t = 1;
        for (int i = size - 1; i >= 0; --i) {
            c[i] = t * nums[i];
            t = t * nums[i];
        }
        vec.push_back(c[1]);
        for (int i = 1; i < size - 1; ++i) {
            vec.push_back(a[i - 1] * c[i + 1]);
        }
        vec.push_back(a[size - 2]);
        return vec;
    }
};
```
### Link: [https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)
