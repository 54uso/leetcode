# 334 - Increasing Triplet Subsequence

### Problem
<p>Given an unsorted array return whether an increasing subsequence of length 3 exists or not in the array.</p>

<p>Formally the function should:</p>

<blockquote>Return true if there exists <i>i, j, k </i><br />
such that <i>arr[i]</i> &lt; <i>arr[j]</i> &lt; <i>arr[k]</i> given 0 &le; <i>i</i> &lt; <i>j</i> &lt; <i>k</i> &le; <i>n</i>-1 else return false.</blockquote>

<p><strong>Note: </strong>Your algorithm should run in O(<i>n</i>) time complexity and O(<i>1</i>) space complexity.</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,2,3,4,5]</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[5,4,3,2,1]</span>
<strong>Output: </strong><span id="example-output-2">false</span>
</pre>
</div>
</div>

### Code
```java
public class Solution {
    public boolean increasingTriplet(int[] nums) {
        int len = nums.length;
        if (len < 3) {
            return false;
        }
        int first = nums[0], second = -1;
        for (int i = 1; i < len; ++i) {
            if (second != -1 && nums[i] > second) {
                return true;
            }
            if (nums[i] <= first) {
                first = nums[i];
            } else {
                if (second == -1 || nums[i] < second) {
                    second = nums[i];
                }
            }
        }
        return false;
    }
}
```
### Link: [https://leetcode.com/problems/increasing-triplet-subsequence/](https://leetcode.com/problems/increasing-triplet-subsequence/)
