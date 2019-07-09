#412 - Fizz Buzz

### Problem
<p>Write a program that outputs the string representation of numbers from 1 to <i>n</i>.</p>

<p>But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.</p>

<p><b>Example:</b>
<pre>
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
</pre>
</p>

### Code
```java
public class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> ret = new LinkedList<String>();
        for (int i = 1; i <= n; ++i) {
            if (i % 15 == 0) {
                ret.add("FizzBuzz");
                continue;
            }
            if (i % 5 == 0) {
                ret.add("Buzz");
                continue;
            }
            if (i % 3 == 0) {
                ret.add("Fizz");
                continue;
            }
            ret.add(String.valueOf(i));
        }
        return ret;
    }
}
```
### Link: [https://leetcode.com/problems/fizz-buzz/](https://leetcode.com/problems/fizz-buzz/)
