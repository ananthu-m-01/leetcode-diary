# 🧩 Problem: Two Sum

**Link:** [LeetCode 1. Two Sum](https://leetcode.com/problems/two-sum/)

## 📝 Problem Statement
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

---

## 💡 Approach (Using HashMap)
- We use a HashMap to store each number’s value and its index.
- For every element `nums[i]`, we check if `target - nums[i]` already exists in the map.
- If it does, we’ve found our two indices.
- If not, store the current number with its index.

---

## 🧠 Time & Space Complexity
- **Time:** O(n)
- **Space:** O(n)

---

## 💻 Code (Java)
```java
import java.util.*;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int diff = target - nums[i];
            if (map.containsKey(diff)) {
                return new int[] { map.get(diff), i };
            }
            map.put(nums[i], i);
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
