#219 - Contains Duplicate II

### Problem
<p>Given an array of integers and an integer <i>k</i>, find out whether there are two distinct indices <i>i</i> and <i>j</i> in the array such that <b>nums[i] = nums[j]</b> and the <b>absolute</b> difference between <i>i</i> and <i>j</i> is at most <i>k</i>.</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>nums = <span id="example-input-1-1">[1,2,3,1]</span>, k = <span id="example-input-1-2">3</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>nums = <span id="example-input-2-1">[1,0,1,1]</span>, k = <span id="example-input-2-2">1</span>
<strong>Output: </strong><span id="example-output-2">true</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>nums = <span id="example-input-3-1">[1,2,3,1,2,3]</span>, k = <span id="example-input-3-2">2</span>
<strong>Output: </strong><span id="example-output-3">false</span>
</pre>
</div>
</div>
</div>


### Code
```cpp
struct Obj {
    int loc;
    int val;
    Obj(int l, int v) : loc(l), val(v) {
        
    }
};

class Solution {
public:
    static bool compare(Obj* fir, Obj* sec) {
        return fir->val > sec->val;
    }
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        vector<Obj*> objs;
        int size = nums.size();
        for (int i = 0; i < size; ++i) {
            objs.push_back(new Obj(i, nums[i]));
        }
        sort(objs.begin(), objs.end(), compare);
        for (int i = 1; i < size; ++i) {
            if (objs[i]->val == objs[i - 1]->val && abs(objs[i]->loc - objs[i- 1]->loc)<=k) {
                return true;
            } 
        }
        return false;
    }
};
```
### Link: [https://leetcode.com/problems/contains-duplicate-ii/](https://leetcode.com/problems/contains-duplicate-ii/)
