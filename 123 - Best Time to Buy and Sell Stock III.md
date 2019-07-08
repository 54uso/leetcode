### Problem
<p>Say you have an array for which the <em>i</em><sup>th</sup> element is the price of a given stock on day <em>i</em>.</p>

<p>Design an algorithm to find the maximum profit. You may complete at most <em>two</em> transactions.</p>

<p><strong>Note:&nbsp;</strong>You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [3,3,5,0,0,3,1,4]
<strong>Output:</strong> 6
<strong>Explanation:</strong> Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
&nbsp;            Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [1,2,3,4,5]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
&nbsp;            Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
&nbsp;            engaging multiple transactions at the same time. You must sell before buying again.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> [7,6,4,3,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> In this case, no transaction is done, i.e. max profit = 0.</pre>


### Code
```java
public class Solution {
    public int maxProfit(int[] prices) {
        int size = prices.length;
        if (size <= 1) {
            return 0;
        }
        int pre[] = new int[size];
        int stu[] = new int[size];
        int mmin = prices[0];
        pre[0] = 0;
        for (int i = 1; i < size; ++i) {
            pre[i] = max(pre[i - 1], prices[i] - mmin);
            mmin = min(mmin, prices[i]);
        }
        int mmax = prices[size - 1];
        stu[size - 1] = 0;
        for (int i = size - 2; i >= 0; --i) {
            stu[i] = max(stu[i + 1], mmax - prices[i]);
            mmax = max(mmax, prices[i]);
        }
        int ret = pre[size - 1];
        for (int i = 0; i < size - 2; ++i) {
            ret = max(ret, pre[i] + stu[i + 1]); 
        }
        return ret;
    }
    
    private int min(int a, int b) {
        return a < b ? a : b;
    }
    
    private int max(int a, int b) {
        return a> b ? a : b;
    }
    
}
```
