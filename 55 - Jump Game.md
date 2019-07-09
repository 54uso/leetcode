#55 - Jump Game

### Problem
<p>Given an array of non-negative integers, you are initially positioned at the first index of the array.</p>

<p>Each element in the array represents your maximum jump length at that position.</p>

<p>Determine if you are able to reach the last index.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,3,1,1,4]
<strong>Output:</strong> true
<strong>Explanation:</strong> Jump 1 step from index 0 to 1, then 3 steps to the last index.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [3,2,1,0,4]
<strong>Output:</strong> false
<strong>Explanation:</strong> You will always arrive at index 3 no matter what. Its maximum
&nbsp;            jump length is 0, which makes it impossible to reach the last index.
</pre>


### Code
```java
public class Solution {
    public boolean canJump(int[] nums) {
        int size = nums.length;
        int maxLen = 0;
        for (int i = 0; i < size; ++i) {
            if (i <= maxLen) {
                if (i + nums[i] > maxLen) {
                    maxLen = i + nums[i];
                    if (maxLen >= size - 1) {
                        return true;
                    }
                }
            }
        }
        return maxLen >= size - 1;
    }
}
```
### Link: [https://leetcode.com/problems/jump-game/](https://leetcode.com/problems/jump-game/)