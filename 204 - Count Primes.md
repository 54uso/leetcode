### Problem
<p>Count the number of prime numbers less than a non-negative number, <b><i>n</i></b>.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 10
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
</pre>


### Code
```java
public class Solution {
    public int countPrimes(int n) {
        int ret = 0;
        boolean[] flags = new boolean[n];
        for (int i = 2; i < n; ++i) {
            if (!flags[i]) {
                ret++;
                int j = (n - 1) / i;
                for (int k = 2; k <= j; ++k) {
                    flags[i * k] = true;
                }
            }
        }
        return ret;
    }
}
```
