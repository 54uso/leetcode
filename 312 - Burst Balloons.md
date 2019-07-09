# 312 - Burst Balloons

### Problem
<p>Given <code>n</code> balloons, indexed from <code>0</code> to <code>n-1</code>. Each balloon is painted with a number on it represented by array <code>nums</code>. You are asked to burst all the balloons. If the you burst balloon <code>i</code> you will get <code>nums[left] * nums[i] * nums[right]</code> coins. Here <code>left</code> and <code>right</code> are adjacent indices of <code>i</code>. After the burst, the <code>left</code> and <code>right</code> then becomes adjacent.</p>

<p>Find the maximum coins you can collect by bursting the balloons wisely.</p>

<p><b>Note:</b></p>

<ul>
	<li>You may imagine <code>nums[-1] = nums[n] = 1</code>. They are not real therefore you can not burst them.</li>
	<li>0 &le; <code>n</code> &le; 500, 0 &le; <code>nums[i]</code> &le; 100</li>
</ul>

<p><b>Example:</b></p>

<pre>
<b>Input:</b> <code>[3,1,5,8]</code>
<b>Output:</b> <code>167 
<strong>Explanation: </strong></code>nums = [3,1,5,8] --&gt; [3,5,8] --&gt;   [3,8]   --&gt;  [8]  --&gt; []
&nbsp;            coins =  3*1*5      +  3*5*8    +  1*3*8      + 1*8*1   = 167
</pre>

### Code
```java
public class Solution {
    
    public int maxCoins(int[] nums) {
        int len = nums.length;
        if (len == 0) {
            return 0;
        }
        int[] tmp = new int[len + 2];
        tmp[0] = 1;
        tmp[len + 1] = 1;
        for (int i = 1; i < len + 1; ++i) {
            tmp[i] = nums[i - 1];
        }
        int[][] dp = new int[len + 2][len + 2];
        for (int i = 2; i < len + 2; ++i) {
            for (int j = i; j < len + 2; ++j) {
                for (int k = 1; k < i; ++k) {
                    //System.out.printf("%d %d %d %d\n", k, dp[j][k], dp[k][j - i], nums[j] * nums[k] * nums[j - i]);
                    dp[j][i] = this.max(dp[j][i], dp[j][k] + dp[j - k][i - k] + tmp[j] * tmp[j - k] * tmp[j - i]);
                }
                //System.out.printf("dp[%d][%d]=%d\n", j, i, dp[j][i]);
            }
        }
        return dp[len + 1][len + 1];
    }
    
    private int max(int a, int b) {
        return a > b ? a : b;
    }
}
```
### Link: [https://leetcode.com/problems/burst-balloons/](https://leetcode.com/problems/burst-balloons/)
