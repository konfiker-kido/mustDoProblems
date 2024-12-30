# 2553. Separate the Digits in an Array

## Problem Statement

Given an array of integers nums, we need to separate the digits in each number and return them as a single list in the same order. 
The digits of each number should appear one by one.

#### Input 1:
```text
nums = [13, 25, 83, 77]
```

#### Output :
```
[1, 3, 2, 5, 8, 3, 7, 7]
```
#### Input 2:
```
nums = [7, 1, 3, 9]
```
#### Output:
```
[7, 1, 3, 9]
```
## Approach
- Separate the Digits For each number in the array
- Extract the digits by repeatedly using modulus and integer division.
- Store the digits in the result array.
- After processing all numbers, reverse the result array to maintain the correct order of digits.

## Solution Code:
``` cpp
class Solution {
public:
    vector<int> separateDigits(vector<int>& nums) {
        vector<int> ans;

        // Iterate over each number in nums in reverse order
        for(int i = nums.size() - 1; i >= 0; i--) {
            int val = nums[i];
            
            // Extract digits of the current number
            while(val > 0) {
                ans.push_back(val % 10); // Push the last digit
                val /= 10; // Remove the last digit
            }
        }
        
        // Reverse the result vector to maintain correct digit order
        reverse(ans.begin(), ans.end());
        
        return ans;
        
        // Second Method Using string:
        // for(int i = 0; i < nums.size(); i++) {
        //     string num = to_string(nums[i]);
        //     for(int j = 0; j < num.size(); j++) {
        //         res.push_back(num[j] - '0');
        //     }
        // }
    }
};
```
## Explanation:
- The function separateDigits() takes an array nums as input.
- For each number, its digits are extracted using modulus and division, and the digits are added to a result list ans.
- Since digits are collected in reverse order, the list is reversed at the end to ensure the correct order.
- A second approach using strings is provided in the comments, where each number is converted to a string, and the digits are converted back to integers.
**Time Complexity**
- The time complexity of the solution is **O(n * m)**,
  where n is the number of integers in the nums array, and m is the average number of digits in each number. For each number, we iterate through its digits.
Example Walkthrough

## Example 1:

Input:
```
nums = [13, 25, 83, 77]
```
### Execution:
```
Number 13 → Digits [1, 3]
Number 25 → Digits [2, 5]
Number 83 → Digits [8, 3]
Number 77 → Digits [7, 7]
```
After processing, the result is: [1, 3, 2, 5, 8, 3, 7, 7].

Output:

```text
[1, 3, 2, 5, 8, 3, 7, 7]
```
## Example 2:
Input:

```text
nums = [7, 1, 3, 9]
```
### Execution:
```
Number 7 → Digits [7]
Number 1 → Digits [1]
Number 3 → Digits [3]
Number 9 → Digits [9]
After processing, the result is: [7, 1, 3, 9].
```

# Output:
```text
[7, 1, 3, 9]
```
