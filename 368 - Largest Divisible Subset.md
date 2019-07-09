#368 - Largest Divisible Subset

### Problem
<p>Given a set of <b>distinct</b> positive integers, find the largest subset such that every pair (S<sub>i</sub>, S<sub>j</sub>) of elements in this subset satisfies:</p>

<p>S<sub>i</sub> % S<sub>j</sub> = 0 or S<sub>j</sub> % S<sub>i</sub> = 0.</p>

<p>If there are multiple solutions, return any subset is fine.</p>

<p><strong>Example 1:</strong></p>

<div>
<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,2,3]</span>
<strong>Output: </strong><span id="example-output-1">[1,2] </span>(of course, [1,3] will also be ok)
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[1,2,4,8]</span>
<strong>Output: </strong><span id="example-output-2">[1,2,4,8]</span>
</pre>
</div>
</div>

### Code
```java
public class Solution {
    public List<Integer> largestDivisibleSubset(int[] nums) {
        int len = nums.length;
        if (len == 0) {
            return new LinkedList<Integer>();
        }
        Arrays.sort(nums);
        int steps[] = new int[len];
        int pre[] = new int[len];
        int index = 0;
        steps[0] = 1;
        pre[0] = -1;
        for (int i = 1; i < len; ++i) {
            steps[i] = 1;
            pre[i] = -1;
            for (int j = 0; j < i; ++j) {
                if (nums[i] % nums[j] == 0 && steps[j] + 1 > steps[i]) {
                    steps[i] = steps[j] + 1;
                    pre[i] = j;
                }
            }
            if (steps[i] > steps[index]) {
                index = i;
            }
        }
        List<Integer> arr = new LinkedList<Integer>();
        while (index != -1) {
            arr.add(0, nums[index]);
            index = pre[index];
        }
        return arr;
    }
}
```
### Link: [https://leetcode.com/problems/largest-divisible-subset/](https://leetcode.com/problems/largest-divisible-subset/)
