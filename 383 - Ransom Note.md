# 383 - Ransom Note

### Problem
<p>
Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom 
note can be constructed from the magazines ; otherwise, it will return false. 
</p>
<p>
Each letter in the magazine string can only be used once in your ransom note.
</p>

<p><b>Note:</b><br />
You may assume that both strings contain only lowercase letters.
</p>

<pre>
canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true
</pre>


### Code
```java
public class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int a[] = new int[26];
        for (int i = 0; i < ransomNote.length(); ++i) {
            a[ransomNote.charAt(i) - 'a']--;
        }
        for (int i = 0; i < magazine.length(); ++i) {
            a[magazine.charAt(i) - 'a']++;
        }
        for (int i = 0; i < 26; ++i) {
            if (a[i] < 0) {
                return false;
            }
        }
        return true;
    }
}
```
### Link: [https://leetcode.com/problems/ransom-note/](https://leetcode.com/problems/ransom-note/)
