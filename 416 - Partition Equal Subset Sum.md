# 416 - Partition Equal Subset Sum

### Problem
<p>Given a <b>non-empty</b> array containing <b>only positive integers</b>, find if the array can be partitioned into two subsets such that the sum of elements in both subsets is equal.</p>

<p><b>Note:</b></p>

<ol>
	<li>Each of the array element will not exceed 100.</li>
	<li>The array size will not exceed 200.</li>
</ol>

<p>&nbsp;</p>

<p><b>Example 1:</b></p>

<pre>
Input: [1, 5, 11, 5]

Output: true

Explanation: The array can be partitioned as [1, 5, 5] and [11].
</pre>

<p>&nbsp;</p>

<p><b>Example 2:</b></p>

<pre>
Input: [1, 2, 3, 5]

Output: false

Explanation: The array cannot be partitioned into equal sum subsets.
</pre>

<p>&nbsp;</p>


### Code
```java
public class Solution {
    public boolean canPartition(int[] nums) {
        int len = nums.length;
        if (len == 0) {
            return true;
        }
        int sum = 0;
        for (int i = 0; i < len; ++i) {
            sum += nums[i];
        }
        if (sum % 2 != 0) {
            return false;
        }
        int aver = sum / 2;
        boolean flag[][] = new boolean[len][aver + 1];
        if (nums[0] > aver) {
            return false;
        }
        flag[0][nums[0]] = true;
        for (int i = 1; i < len; ++i) {
            for (int j = 0; j <= aver; ++j) {
                if (!flag[i - 1][j]) {
                    continue;
                }
                if (j + nums[i] <= aver) {
                    flag[i][j + nums[i]] = true;
                }
                if (j >= nums[i]) {
                    flag[i][j - nums[i]] = true;
                } else {
                    flag[i][nums[i] - j] = true;
                }
            }
        }
        return flag[len - 1][0];
    }
}
```
### Link: [https://leetcode.com/problems/partition-equal-subset-sum/](https://leetcode.com/problems/partition-equal-subset-sum/)
