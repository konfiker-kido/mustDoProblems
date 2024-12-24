# 231. Power of Two

## Problem Statement

Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`.

---

### Examples

#### Example 1
**Input:**
```
n = 1
```
**Output:**
```
true
```
**Explanation:**
```
2^0 = 1
```

#### Example 2
**Input:**
```
n = 16
```
**Output:**
```
true
```
**Explanation:**
```
2^4 = 16
```

#### Example 3
**Input:**
```
n = 3
```
**Output:**
```
false
```

---

## Solution Approaches

### 1. Recursive Approach
This approach uses recursion to check if the number can be repeatedly divided by 2 until it becomes 1.

#### Code
```cpp
class Solution {
public:
    bool func(int n) {
        if (n == 1) // n is exactly divisible by 2 and reduced to 1
            return true;
        if (n % 2 != 0 || n == 0) // n is not divisible by 2 or is less than 1
            return false;
        return func(n / 2);
    }

    bool isPowerOfTwo(int n) {
        return func(n);
    }
};
```

#### Complexity
- **Time Complexity:** \( O(\log_2(n)) \)  
  Each recursive call divides the number by 2.
- **Space Complexity:** \( O(\log_2(n)) \) due to recursive stack space.

---

### 2. Bit Manipulation Approach

#### Observation
1. A number that is a power of two has exactly one `1` bit in its binary representation.
2. Performing a bitwise AND operation between the number and its predecessor results in `0`.

For example:
- Binary representation of `7` -> `0111`
- Binary representation of `8` -> `1000`
- Bitwise AND (`7 & 8`) -> `0000`

#### Code
```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if (n <= 0) return false;
        return (n & (n - 1)) == 0;
    }
};
```

#### Complexity
- **Time Complexity:** \( O(1) \)
- **Space Complexity:** \( O(1) \)

---

### Comparison of Approaches

| Approach               | Time Complexity | Space Complexity | Notes                                 |
|------------------------|-----------------|------------------|---------------------------------------|
| Recursive             | \( O(\log_2(n)) \) | \( O(\log_2(n)) \) | Simple but uses extra stack space.   |
| Bit Manipulation      | \( O(1) \)       | \( O(1) \)        | Most efficient for this problem.     |
