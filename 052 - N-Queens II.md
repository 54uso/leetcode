### Problem
<p>The <em>n</em>-queens puzzle is the problem of placing <em>n</em> queens on an <em>n</em>&times;<em>n</em> chessboard such that no two queens attack each other.</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/8-queens.png" style="width: 258px; height: 276px;" /></p>

<p>Given an integer&nbsp;<em>n</em>, return the number of&nbsp;distinct solutions to the&nbsp;<em>n</em>-queens puzzle.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 4
<strong>Output:</strong> 2
<strong>Explanation:</strong> There are two distinct solutions to the 4-queens puzzle as shown below.
[
&nbsp;[&quot;.Q..&quot;, &nbsp;// Solution 1
&nbsp; &quot;...Q&quot;,
&nbsp; &quot;Q...&quot;,
&nbsp; &quot;..Q.&quot;],

&nbsp;[&quot;..Q.&quot;, &nbsp;// Solution 2
&nbsp; &quot;Q...&quot;,
&nbsp; &quot;...Q&quot;,
&nbsp; &quot;.Q..&quot;]
]
</pre>


### Code
```cpp
class Solution {
public:
    bool check(int step, int val, int a[]) {
        for (int i = 1; i < step; ++i) {
            if (a[i] == val || abs(step - i) == abs(val - a[i])) {
                return false;
            }
        }
        return true;
    } 
    int dfs(int step, int size, int a[]) {
        int t = 0;
        for (int i = 1; i <= size; ++i) {
            if (check(step, i, a)) {
                if (step == size) {
                    t++;
                } else {
                    a[step] = i;
                    t += dfs(step + 1, size, a);
                }
            }
        }
        return t;
    }
    int totalNQueens(int n) {
        int a[n + 1];
        return dfs(1, n, a);
    }
};
```
