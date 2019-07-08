### Problem
<p>Given an array of non-negative integers, you are initially positioned at the first index of the array.</p>

<p>Each element in the array represents your maximum jump length at that position.</p>

<p>Your goal is to reach the last index in the minimum number of jumps.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [2,3,1,1,4]
<strong>Output:</strong> 2
<strong>Explanation:</strong> The minimum number of jumps to reach the last index is 2.
    Jump 1 step from index 0 to 1, then 3 steps to the last index.</pre>

<p><strong>Note:</strong></p>

<p>You can assume that you can always reach the last index.</p>


### Code
```java
import java.util.concurrent.LinkedBlockingQueue;

public class Solution {
    
    public int jump(int[] nums) {
        int len = nums.length;
        if (len <= 1) {
            return 0;
        }
        int step[] = new int[len];
        for (int i = 0; i < len; ++i) {
            step[i] = Integer.MAX_VALUE;
        }
        Queue<Integer> queue = new LinkedBlockingQueue<Integer>();
        step[0] = 0;
        queue.add(0);
        while (!queue.isEmpty()) {
            int index = queue.poll();
            for (int i = nums[index]; i >= 0; --i) {
                if (index + i == len - 1) {
                    return step[index] + 1;
                }
                if (index + i < len && step[index + i] > step[index] + 1) {
                    step[index + i] = step[index] + 1;
                    queue.add(index + i);
                }
            }
        }
        return step[len - 1];
    }
    
}
```
