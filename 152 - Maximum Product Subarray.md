# 152 - Maximum Product Subarray

### Problem
<p>Given an integer array&nbsp;<code>nums</code>, find the contiguous subarray within an array (containing at least one number) which has the largest product.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,3,-2,4]
<strong>Output:</strong> <code>6</code>
<strong>Explanation:</strong>&nbsp;[2,3] has the largest product 6.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [-2,0,-1]
<strong>Output:</strong> 0
<strong>Explanation:</strong>&nbsp;The result cannot be 2, because [-2,-1] is not a subarray.</pre>


### Code
```java
public class Solution {
    
    public int maxProduct(int[] nums) {
        int len = nums.length;
        if (len == 0) {
            return 0;
        }
        if (len == 1) {
            return nums[0];
        }
        int ret = nums[0];
        int[][] dp = new int[len][2];
        dp[0][0] = nums[0];
        dp[0][1] = nums[0];
        for (int i = 1; i < len; ++i) {
            int t0 = dp[i - 1][0] * nums[i];
            int t1 = dp[i - 1][1] * nums[i];
            dp[i][0] = this.min(
                nums[i], this.min(t0, t1)
            );
            dp[i][1] = this.max(
                nums[i], this.max(t0, t1)
            );
            //System.out.println(i + " " + dp[i][0] + " " + dp[i][1]);
            ret = this.max(dp[i][1], ret);
        }
        return ret;
    }
    
    private int max(int a, int b) {
        return a > b ? a : b;
    }
    
    private int min(int a, int b) {
        return a < b ? a : b;
    }
    
}
```
### Link: [https://leetcode.com/problems/maximum-product-subarray/](https://leetcode.com/problems/maximum-product-subarray/)
