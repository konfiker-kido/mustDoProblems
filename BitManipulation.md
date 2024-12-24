# 338. Counting Bits

## Problem Statement

Given an integer `n`, return an array `ans` of length `n + 1` such that for each `i` (0 <= i <= n), `ans[i]` is the number of 1's in the binary representation of `i`.

---

### Examples

#### Example 1
**Input:**
```
n = 2
```
**Output:**
```
[0, 1, 1]
```
**Explanation:**
```
0 --> 0
1 --> 1
2 --> 10
```

#### Example 2
**Input:**
```
n = 5
```
**Output:**
```
[0, 1, 1, 2, 1, 2]
```
**Explanation:**
```
0 --> 0
1 --> 1
2 --> 10
3 --> 11
4 --> 100
5 --> 101
```

---

## Brute Force Solution
The brute force approach involves:
1. Converting each number to its binary representation.
2. Counting the number of 1's in the binary string.

### Code
```cpp
class Solution {
public:
    int returnCountBits(string str) {
        int count = 0;
        for (char bits : str) {
            if (bits == '1')
                count++;
        }
        return count;
    }

    string decToBinary(int num) {
        string ans = "";
        while (num != 1 && num != 0) {
            ans += to_string(num % 2);
            num /= 2;
        }
        ans += to_string(num);
        return ans;
    }

    vector<int> countBits(int n) {
        vector<int> ans;
        for (int i = 0; i <= n; i++) {
            string binary = decToBinary(i);
            ans.push_back(returnCountBits(binary));
        }
        return ans;
    }
};
```

### Complexity
- **Time Complexity:** \( O(n \cdot k) \), where \( k \) is the maximum number of bits for \( n \).
- **Space Complexity:** \( O(k) \) for storing the binary representation of a number.

---

## Optimized Solution
The optimized solution uses a dynamic programming approach with the observation:
- `ans[i] = ans[i - x] + 1`, where `x` is the largest power of 2 less than or equal to `i`.

### Code
```cpp
class Solution {
public:
    vector<int> countBits(int n) {
        vector<int> ans(n + 1);
        int x = 1;
        for (int i = 1; i <= n; i++) {
            if (i >= (x << 1))
                x <<= 1;
            ans[i] = 1 + ans[i - x];
        }
        return ans;
    }
};
```

### Complexity
- **Time Complexity:** \( O(n) \).
- **Space Complexity:** \( O(1) \) additional space.

---

### Alternative Approach Using Built-in Functions
We can use the built-in function `__builtin_popcount` in C++ to directly count the number of 1's in the binary representation of a number.

### Code
```cpp
class Solution {
public:
    vector<int> countBits(int n) {
        vector<int> ans; 
        for (int i = 0; i <= n; i++) {
            ans.push_back(__builtin_popcount(i));
        }
        return ans;
    }
};
```

---

### Comparison of Approaches
| Approach                 | Time Complexity | Space Complexity | Notes                                    |
|--------------------------|-----------------|------------------|------------------------------------------|
| Brute Force             | \( O(n \cdot k) \) | \( O(k) \)        | Converts to binary and counts 1's.      |
| Dynamic Programming     | \( O(n) \)       | \( O(1) \)        | Efficient with simple recurrence.       |
| Built-in Function       | \( O(n) \)       | \( O(1) \)        | Relies on C++ built-in functionality.   |
