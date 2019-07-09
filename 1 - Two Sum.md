#1 - Two Sum

### Problem
<p>Given an array of integers, return <strong>indices</strong> of the two numbers such that they add up to a specific target.</p>

<p>You may assume that each input would have <strong><em>exactly</em></strong> one solution, and you may not use the <em>same</em> element twice.</p>

<p><strong>Example:</strong></p>

<pre>
Given nums = [2, 7, 11, 15], target = 9,

Because nums[<strong>0</strong>] + nums[<strong>1</strong>] = 2 + 7 = 9,
return [<strong>0</strong>, <strong>1</strong>].
</pre>


### Code
```java
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        int origins[] = Arrays.copyOf(nums, nums.length);
        Arrays.sort(nums);
        int left = 0, right = nums.length - 1;
        while (nums[left] + nums[right] != target) {
            if (nums[left] + nums[right] < target) {
                left++;
            } else {
                right--;
            }
        }
        int ret[] = new int[]{-1, -1};
        for (int i = 0; i < origins.length; ++i) {
            if (origins[i] == nums[left] && ret[0] == -1) {
                ret[0] = i;
                continue;
            }
            if (origins[i] == nums[right]) {
                ret[1] = i;
            }
        }
        return ret;
    }
}
```
### Link: [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)
