#85 - Maximal Rectangle

### Problem
<p>Given a 2D binary matrix filled with 0&#39;s and 1&#39;s, find the largest rectangle containing only 1&#39;s and return its area.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>
[
  [&quot;1&quot;,&quot;0&quot;,&quot;1&quot;,&quot;0&quot;,&quot;0&quot;],
  [&quot;1&quot;,&quot;0&quot;,&quot;<strong>1</strong>&quot;,&quot;<strong>1</strong>&quot;,&quot;<strong>1</strong>&quot;],
  [&quot;1&quot;,&quot;1&quot;,&quot;<strong>1</strong>&quot;,&quot;<strong>1</strong>&quot;,&quot;<strong>1</strong>&quot;],
  [&quot;1&quot;,&quot;0&quot;,&quot;0&quot;,&quot;1&quot;,&quot;0&quot;]
]
<strong>Output:</strong> 6
</pre>


### Code
```java
public class Solution {
    
    public int maximalRectangle(char[][] matrix) {
        int rows = matrix.length;
        if (rows == 0) {
            return 0;
        }
        int cols = matrix[0].length;
        int[] sum = new int[rows];
        int ret = 0;
        for (int i = 0; i < cols; ++i) {
            for (int j = 0; j < rows; ++j) {
                sum[j] = matrix[j][i] == '0' ? 0 : sum[j] + matrix[j][i] - '0';
            }
            ret = this.max(ret, this.solve(sum));
        }
        return ret;
    }
    
    private int solve(int[] nums) {
        int ret = 0;
        int len = nums.length;
        int[] orders = new int[len];
        int[] indexs = new int[len];
        for (int i = 0; i < len; ++i) {
            orders[i] = Integer.MAX_VALUE;
        }
        for (int i = 0; i < len; ++i) {
            int t = this.insert(nums[i], orders);
            indexs[t] = i;
            int low = -1;
            for (int j = 0; j <= t; ++j) {
                if (low > indexs[j]) {
                    continue;
                }
                ret = this.max(ret, (i - low) * orders[j]);
                low = indexs[j];
            }
        }
        return ret;
    }
    
    private int insert(int val, int[] orders) {
        int left = 0, right = orders.length;
        while (left < right) {
            int mid = (left + right) >> 1;
            if (orders[mid] < val) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        orders[left] = val;
        return left;
    }
    
    private int max(int a, int b) {
        return a > b ? a : b;
    }
    
}
```
### Link: [https://leetcode.com/problems/maximal-rectangle/](https://leetcode.com/problems/maximal-rectangle/)
