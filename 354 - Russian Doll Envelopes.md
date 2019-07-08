### Problem
<p>You have a number of envelopes with widths and heights given as a pair of integers <code>(w, h)</code>. One envelope can fit into another if and only if both the width and height of one envelope is greater than the width and height of the other envelope.</p>

<p>What is the maximum number of envelopes can you Russian doll? (put one inside other)</p>

<p><b>Note:</b><br />
Rotation is not allowed.</p>

<p><strong>Example:</strong></p>

<div>
<pre>
<strong>Input: </strong><span id="example-input-1-1">[[5,4],[6,4],[6,7],[2,3]]</span>
<strong>Output: </strong><span id="example-output-1">3 
<strong>Explanation: T</strong></span>he maximum number of envelopes you can Russian doll is <code>3</code> ([2,3] =&gt; [5,4] =&gt; [6,7]).
</pre>
</div>


### Code
```java
public class Solution {
    public int maxEnvelopes(int[][] envelopes) {
        int len = envelopes.length;
        if (len < 2) {
            return len;
        }
        Arrays.sort(envelopes, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return (o2[0] == o1[0] ? o2[1] - o1[1] : o1[0] - o2[0]);
            }
        });
        int[] val = new int[len];
        val[0] = envelopes[0][1];
        int size = 1;
        for (int i = 1; i < len; ++i) {
            size = this.sovle(envelopes[i][1], size, val);
        }
        return size;
    }
    
    private int sovle(int num, int size, int[] val) {
        int left = 0, right = size;
        while (left < right) {
            int mid = (left + right) / 2;
            if (val[mid] < num) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        val[left] = num;
        return left + 1 > size ? left + 1: size;
    }
    
}
```
