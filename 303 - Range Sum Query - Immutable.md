# 303 - Range Sum Query - Immutable

### Problem
<p>Given an integer array <i>nums</i>, find the sum of the elements between indices <i>i</i> and <i>j</i> (<i>i</i> &le; <i>j</i>), inclusive.</p>

<p><b>Example:</b><br>
<pre>
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>You may assume that the array does not change.</li>
<li>There are many calls to <i>sumRange</i> function.</li>
</ol>
</p>

### Code
```java
public class NumArray {

    private int[] sum;

    public NumArray(int[] nums) {
        this.init(nums);
    }
    
    private void init(int[] nums) {
        int len = nums.length;
        if (len == 0) {
            return;
        }
        int[] sum = new int[len + 1];
        for (int i = 0; i < len; ++i) {
            sum[i + 1] = sum[i] + nums[i];
        }
        this.sum = sum;
    }

    public int sumRange(int i, int j) {
        return this.sum[j + 1] - this.sum[i];
    }
    
}

```
### Link: [https://leetcode.com/problems/range-sum-query-immutable/](https://leetcode.com/problems/range-sum-query-immutable/)
