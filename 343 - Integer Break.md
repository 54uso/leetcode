# 343 - Integer Break

### Problem
<p>Given a positive integer <i>n</i>, break it into the sum of <b>at least</b> two positive integers and maximize the product of those integers. Return the maximum product you can get.</p>

<p><strong>Example 1:</strong></p>

<div>
<pre>
<strong>Input: </strong><span id="example-input-1-1">2</span>
<strong>Output: </strong><span id="example-output-1">1</span>
<strong>Explanation: </strong>2 = 1 + 1, 1 &times; 1 = 1.</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">10</span>
<strong>Output: </strong><span id="example-output-2">36</span>
<strong>Explanation: </strong>10 = 3 + 3 + 4, 3 &times;&nbsp;3 &times;&nbsp;4 = 36.</pre>

<p><b>Note</b>: You may assume that <i>n</i> is not less than 2 and not larger than 58.</p>
</div>
</div>

### Code
```java
public class Solution {
    
    private static int ans[];
    
    public Solution() {
        this.init();
    }
    
    public int integerBreak(int n) {
        return this.ans[n] - (this.ans[n] == n && n != 4 ? 1 : 0);
    }
    
    private void init() {
        int[] ans = new int[59];
        ans[0] = 1;
        for (int i = 2; i < 59; ++i) {
            for (int j = 1; j <= i; ++j) {
                ans[i] = this.max(ans[i], j * ans[i - j]);
            }
        }
        this.ans = ans;
    }
    
    private int max(int a, int b) {
        return a > b ? a : b;
    }
    
}
```
### Link: [https://leetcode.com/problems/integer-break/](https://leetcode.com/problems/integer-break/)
