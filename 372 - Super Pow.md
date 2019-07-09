#372 - Super Pow

### Problem
<p>Your task is to calculate <i>a</i><sup><i>b</i></sup> mod 1337 where <i>a</i> is a positive integer and <i>b</i> is an extremely large positive integer given in the form of an array.</p>

<p><strong>Example 1:</strong></p>

<div>
<pre>
<strong>Input: </strong>a = <span id="example-input-1-1">2</span>, b = <span id="example-input-1-2">[3]</span>
<strong>Output: </strong><span id="example-output-1">8</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>a = <span id="example-input-2-1">2</span>, b = <span id="example-input-2-2">[1,0]</span>
<strong>Output: </strong><span id="example-output-2">1024</span>
</pre>
</div>
</div>

### Code
```java
public class Solution {
    
    private static final int mod = 1337;
    
    public int superPow(int a, int[] b) {
        int ret = 1;
        for (int i = 0; i < b.length; ++i) {
            ret = this.pow(ret, 10, mod) * this.pow(a, b[i], mod) % mod;
        }
        return ret;
    }
    
    private int pow(int a, int c, int mod) {
        int ret = 1;
        while (c != 0) {
            a = a % mod;
            if ((c & 1) == 1) {
                ret = ret * a % mod;
            }
            a = a * a;
            c = c >> 1;
        }
        return ret;
    }
    
}
```
### Link: [https://leetcode.com/problems/super-pow/](https://leetcode.com/problems/super-pow/)
