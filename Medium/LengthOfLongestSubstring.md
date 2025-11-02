# 🔠 LeetCode Problem: Longest Substring Without Repeating Characters

**Problem Link:** [LeetCode #3 - Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

---

## 📝 Problem Statement

Given a string `s`, find the **length of the longest substring** without repeating characters.

A substring is a contiguous sequence of characters within a string.

---

### 🔹 Example 1
**Input:**  
`s = "abcabcbb"`

**Output:**  
`3`

**Explanation:**  
The answer is `"abc"`, with the length of 3.

---

### 🔹 Example 2
**Input:**  
`s = "bbbbb"`

**Output:**  
`1`

**Explanation:**  
The longest substring without repeating characters is `"b"`.

---

### 🔹 Example 3
**Input:**  
`s = "pwwkew"`

**Output:**  
`3`

**Explanation:**  
The answer is `"wke"`, with the length of 3.  
Note that `"pwke"` is a subsequence and not a substring.

---

## 💡 Approach (Sliding Window + HashSet)

This problem can be solved efficiently using the **sliding window technique** and a **HashSet**:

1. Use two pointers:
   - `left`: start of the current window.
   - `right`: end of the current window.
2. Expand `right` to explore new characters.
3. If a duplicate character is found (exists in the HashSet):
   - Shrink the window by moving `left` and removing characters from the set until the duplicate is gone.
4. Update `maxLength` with the size of the current window.
5. Continue until the end of the string.

This ensures we visit each character at most twice → **O(n)** time.

---

## 💻 Code Implementation

```java
import java.util.HashSet;

class Solution {
    public int lengthOfLongestSubstring(String s) {
        int left = 0, maxLength = 0;
        HashSet<Character> set = new HashSet<>();

        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }
}
```