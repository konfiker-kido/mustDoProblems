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

# Problem: Roman to Integer

## Problem Statement

Given a Roman numeral string `s`, convert it to an integer. The input string is guaranteed to be a valid Roman numeral.

---

### Examples

#### Example 1
**Input:**
```
s = "III"
```
**Output:**
```
3
```
**Explanation:** III = 3.

#### Example 2
**Input:**
```
s = "LVIII"
```
**Output:**
```
58
```
**Explanation:** L = 50, V = 5, III = 3.

#### Example 3
**Input:**
```
s = "MCMXCIV"
```
**Output:**
```
1994
```
**Explanation:** M = 1000, CM = 900, XC = 90, IV = 4.

---

## Solution Approach

### Algorithm
1. Use an array of Roman symbols and their corresponding values:
   - Symbols: `{"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"}`
   - Values: `{1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1}`
2. Iterate through the symbol-value pairs.
3. While the current value can be subtracted from `num`, append the symbol to the result string and subtract the value from `num`.
4. Repeat until `num` becomes zero.

### Code

```cpp
class Solution {
public:
    string intToRoman(int num) {
        string symbols[] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int values[] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};

        string ans = "";
        for (int i = 0; i < 13; i++) {
            while (values[i] <= num) {
                ans += symbols[i];  // Append the symbol to the result
                num -= values[i];   // Subtract the value from num
            }
        }

        return ans;
    }
};
```

---

### Complexity Analysis

- **Time Complexity:** \( O(n) \), where \( n \) is the number of symbol-value pairs (constant at 13).
- **Space Complexity:** \( O(1) \), as we use a fixed amount of extra space.

---

### Notes
- The approach ensures that larger values are processed first, guaranteeing a valid Roman numeral representation.
