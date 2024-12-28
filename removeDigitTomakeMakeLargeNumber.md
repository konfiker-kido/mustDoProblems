# 2259. Remove Digit From Number to Maximize Result

You are given a string `number` representing a positive integer and a character `digit`.

Return the resulting string after removing exactly one occurrence of `digit` from `number` such that the value of the resulting string in decimal form is maximized. 

The test cases are generated such that `digit` occurs at least once in `number`.

## Examples

### Example 1:
```text
Input: number = "123", digit = "3"
Output: "12"
Explanation: There is only one '3' in "123". After removing '3', the result is "12".
```

### Example 2:
```text
Input: number = "1231", digit = "1"
Output: "231"
Explanation: We can remove the first '1' to get "231" or remove the second '1' to get "123". Since 231 > 123, we return "231".
```

### Example 3:
```text
Input: number = "551", digit = "5"
Output: "51"
Explanation: We can remove either the first or second '5' from "551". Both result in the string "51".
```

## Solution

### Implementation

#### Brute Force
```cpp
string removeDigit(string n, char d) {
    // Brute Force
    int count = 0;    
    vector<string> ans;
    for (int i = 0; i < n.length(); i++) {
        string temp = "";
        if (d == n[i]) {
            temp = n.substr(0, i) + n.substr(i + 1, n.size());
            ans.push_back(temp);
        }
    }
    sort(ans.begin(), ans.end());
    return ans[ans.size() - 1];
}
```

**Explanation**:
- Iterate through the string to find all occurrences of the digit.
- Remove each occurrence and store the resulting strings in a vector.
- Sort the vector lexicographically and return the largest string.

**Complexity**:
- **Time Complexity**: O(n²), where n is the length of the string. Removing a substring and sorting the results both contribute to this complexity.
- **Space Complexity**: O(n), as we store intermediate results in a vector.

#### Optimized Solution
```cpp
string removeDigit(string n, char d) {
    string result = "";
    for (int i = 0; i < n.length(); i++) {
        if (n[i] == d) {
            string temp = n.substr(0, i) + n.substr(i + 1);
            if (temp > result) {
                result = temp;
            }
        }
    }
    return result;
}
```

**Explanation**:
- Traverse the string and simulate removing each occurrence of the digit.
- Compare the resulting string with the current maximum result.
- Update the maximum result if the new string is lexicographically greater.

**Complexity**:
- **Time Complexity**: O(n), as we traverse the string once and perform constant-time operations for each character.
- **Space Complexity**: O(1), since no additional data structures are used apart from a temporary string for comparisons.
