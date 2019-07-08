### Problem
<p>Given an array of integers, find if the array contains any duplicates.</p>

<p>Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [1,2,3,1]
<strong>Output:</strong> true</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>[1,2,3,4]
<strong>Output:</strong> false</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>[1,1,1,3,3,4,3,2,4,2]
<strong>Output:</strong> true</pre>


### Code
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        int size = nums.size();
        if (size <= 1) {
            return false;
        }
        sort(nums.begin(), nums.end());
        for (int i = 1; i < size; ++i) {
            if (nums[i] == nums[i - 1]) {
                return true;
            }
        }
        return false;
    }
};
```
