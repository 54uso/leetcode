#300 - Longest Increasing Subsequence

### Problem
<p>Given an unsorted array of integers, find the length of longest increasing subsequence.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b> <code>[10,9,2,5,3,7,101,18]
</code><b>Output: </b>4 
<strong>Explanation: </strong>The longest increasing subsequence is <code>[2,3,7,101]</code>, therefore the length is <code>4</code>. </pre>

<p><strong>Note: </strong></p>

<ul>
	<li>There may be more than one LIS combination, it is only necessary for you to return the length.</li>
	<li>Your algorithm should run in O(<i>n<sup>2</sup></i>) complexity.</li>
</ul>

<p><b>Follow up:</b> Could you improve it to O(<i>n</i> log <i>n</i>) time complexity?</p>


### Code
```java
public class Solution {
    public int lengthOfLIS(int[] nums) {
        int len = nums.length;
        if (len < 2) {
            return len;
        }
        int[] val = new int[len];
        val[0] = nums[0];
        int size = 1;
        for (int i = 1; i < len; ++i) {
            size = this.sovle(nums[i], size, val);
        }
        return size;
    }
    
    private int sovle(int num, int size, int[] val) {
        int left = 0, right = size;
        while (left < right) {
            int mid = (left + right) / 2;
            if (val[mid] < num) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        val[left] = num;
        return left + 1 > size ? left + 1: size;
    }
    
}
```
### Link: [https://leetcode.com/problems/longest-increasing-subsequence/](https://leetcode.com/problems/longest-increasing-subsequence/)
