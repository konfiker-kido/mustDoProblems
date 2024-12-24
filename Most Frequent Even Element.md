# Problem: Largest Number

## Problem Statement

Given a list of non-negative integers `nums`, arrange them such that they form the largest number and return it.

Since the result may be very large, return a string instead of an integer.

---

### Examples

#### Example 1
**Input:**
```
nums = [10,2]
```
**Output:**
```
"210"
```

#### Example 2
**Input:**
```
nums = [3,30,34,5,9]
```
**Output:**
```
"9534330"
```

#### Example 3
**Input:**
```
nums = [1,2,3,5,4]
```
**Output:**
```
"54321"
```

---

## Solution Approach

### Algorithm
1. Convert each integer in the array to a string for easier manipulation.
2. Use a custom comparator to sort the strings based on the concatenation order:
   - Compare two strings `a` and `b` by checking if `a + b` is greater than `b + a`.
3. Sort the array using the custom comparator.
4. If the largest element (first in the sorted array) is "0", return "0" (since all elements are zeros).
5. Concatenate the sorted strings to form the final result.

### Code

```cpp
class Solution {
public:
    // Custom comparator
    static bool cmp(string a, string b) {
        string t1 = a + b;
        string t2 = b + a;
        return t1 > t2;
    }

    string largestNumber(vector<int>& nums) {
        vector<string> str;

        // Convert integers to strings
        for (int val : nums)
            str.push_back(to_string(val));

        // Sort using custom comparator
        sort(str.begin(), str.end(), cmp);

        // If the largest element is "0", return "0"
        if (str[0] == "0") return "0";

        // Concatenate sorted strings to form the result
        string ans = "";
        for (string s : str)
            ans += s;

        return ans;
    }
};
```

---

### Complexity Analysis

- **Time Complexity:** \( O(n \log n) \), where \( n \) is the number of elements in the input array. Sorting the strings dominates the time complexity.
- **Space Complexity:** \( O(n) \), for storing the string representations of the integers.

---

### Notes
- This approach ensures that the concatenated result is the largest possible number in lexicographical order.
- The custom comparator is the key to solving the problem efficiently and correctly.
