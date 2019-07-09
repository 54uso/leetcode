# 4 - Median of Two Sorted Arrays

### Problem
<p>There are two sorted arrays <b>nums1</b> and <b>nums2</b> of size m and n respectively.</p>

<p>Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).</p>

<p>You may assume <strong>nums1</strong> and <strong>nums2</strong>&nbsp;cannot be both empty.</p>

<p><b>Example 1:</b></p>

<pre>
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
</pre>

<p><b>Example 2:</b></p>

<pre>
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
</pre>


### Code
```java
public class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int len1 = nums1.length;
        int len2 = nums2.length;
        int sum = 0, left = (len1 + len2 - 1) / 2, right = (len1 + len2) / 2;
        for (int i = 0, j = 0, k = 0; i <= right; ++i) {
            int t;
            if (j == len1) {
                t = nums2[k++];
            } else if (k == len2) {
                t = nums1[j++];
            } else {
                if (nums1[j] <= nums2[k]) {
                    t = nums1[j++];
                } else {
                    t = nums2[k++];
                }
            }
            if (i == left) {
                sum += t;
            }
            if (i == right) {
                sum += t;
            }
        }
        return sum / 2.0;
    }
}
```
### Link: [https://leetcode.com/problems/median-of-two-sorted-arrays/](https://leetcode.com/problems/median-of-two-sorted-arrays/)
