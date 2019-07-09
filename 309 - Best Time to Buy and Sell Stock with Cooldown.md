#309 - Best Time to Buy and Sell Stock with Cooldown

### Problem
<p>Say you have an array for which the <i>i</i><sup>th</sup> element is the price of a given stock on day <i>i</i>.</p>

<p>Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times) with the following restrictions:</p>

<ul>
	<li>You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).</li>
	<li>After you sell your stock, you cannot buy stock on next day. (ie, cooldown 1 day)</li>
</ul>

<p><b>Example:</b></p>

<pre>
<strong>Input:</strong> [1,2,3,0,2]
<strong>Output: </strong>3 
<strong>Explanation:</strong> transactions = [buy, sell, cooldown, buy, sell]
</pre>

### Code
```java
public class Solution {
    
    public int maxProfit(int[] prices) {
        int len = prices.length;
        if (len == 0) {
            return 0;
        }
        int[][] dp = new int[len][2];
        for (int i = 1; i < len; ++i) {
            dp[i][0] = this.max(dp[i - 1][0], dp[i - 1][1]);
            if (prices[i] > prices[i - 1]) {
                dp[i][1] = prices[i] - prices[i - 1] + this.max(i > 1 ? dp[i - 2][0] : 0, dp[i - 1][1]);
            }
            if (i > 1 && prices[i] > prices[i - 2]) {
                dp[i][1] = this.max(
                    dp[i][1],
                    prices[i] - prices[i - 2] + this.max(i > 2 ? dp[i - 3][0] : 0, dp[i - 2][1])
                );
            }
        }
        return this.max(dp[len - 1][0], dp[len - 1][1]);
    }
    
    private int max(int a, int b) {
        return a > b ? a : b;
    }
    
}
```
### Link: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)
