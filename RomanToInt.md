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
