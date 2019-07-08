### Problem
<p>You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are <strong>arranged in a circle.</strong> That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have security system connected and&nbsp;<b>it will automatically contact the police if two adjacent houses were broken into on the same night</b>.</p>

<p>Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight <strong>without alerting the police</strong>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,3,2]
<strong>Output:</strong> 3
<strong>Explanation:</strong> You cannot rob house 1 (money = 2) and then rob house 3 (money = 2),
&nbsp;            because they are adjacent houses.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [1,2,3,1]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Rob house 1 (money = 1) and then rob house 3 (money = 3).
&nbsp;            Total amount you can rob = 1 + 3 = 4.</pre>


### Code
```java
public class Solution {
    
    public int rob(int[] nums) {
        int len = nums.length;
        if (len == 0) {
            return 0;
        }
        if (len == 1) {
            return nums[0];
        }
        int ret = nums[0];
        int tmp = nums[0];
        nums[0] = 0;
        ret = this.max(ret, this.solve(nums));
        nums[0] = tmp;
        nums[len - 1] = 0;
        ret = this.max(ret, this.solve(nums));
        return ret;
    }
    
    private int solve(int[] nums) {
        int len = nums.length;
        int[] dp = new int[len];
        dp[0] = nums[0];
        dp[1] = this.max(nums[0], nums[1]);
        for (int i = 2; i < len; ++i) {
            dp[i] = this.max(dp[i - 1], dp[i - 2] + nums[i]);
        }
        return dp[len - 1];
    }
    
    private int max(int a, int b) {
        return a > b ? a : b;
    }
    
}
```
