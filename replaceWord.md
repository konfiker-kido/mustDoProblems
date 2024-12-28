# Replace "pi" with "3.14" in a String

Given a string, compute a new string where all appearances of "pi" have been replaced by "3.14".

## Examples

### Example 1:
```text
Input: xpix
Output: x3.14x
```

### Example 2:
```text
Input: xpipi
Output: x3.143.14
```

### Example 3:
```text
Input: xpixabcpid
Output: x3.14xabc3.14d
```

## Solution

### Implementation
```cpp
string replacePi(string str) {
    for (int i = 0; i < str.length() - 1; i++) {
        // Check for "pi" and replace with "3.14"
        if (str[i] == 'p' && str[i + 1] == 'i') {
            string t = "3.14";
            str = str.substr(0, i) + t + str.substr(i + 2, str.length());
        }
    }
    return str;
}
```

## Explanation
- Traverse the string using a loop.
- When "pi" is encountered, replace it with "3.14" using string manipulation.
- Use `substr` to construct the new string, including parts before and after "pi".
- Continue the loop to find and replace all occurrences.


