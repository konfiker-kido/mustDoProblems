# Self Dividing Numbers Solution

## Problem Statement

A self-dividing number is a number that is divisible by every digit it contains. A self-dividing number is not allowed to contain the digit zero.

For example:
- `128` is a self-dividing number because:
  - 128 % 1 == 0
  - 128 % 2 == 0
  - 128 % 8 == 0
- `128` is **self-dividing**.

A number like `101` is **not** self-dividing because it contains a `0`, and dividing by zero is not allowed.

Given two integers `left` and `right`, return a list of all the self-dividing numbers in the inclusive range `[left, right]`.

### Input
- `left = 1`
- `right = 22`

### Output
```text
[1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
```

## Approach
### Check if a number is self-dividing:

For each number in the given range, we need to check if every digit of the number divides the number itself.
A number cannot contain a 0 digit, as dividing by 0 is not allowed.
Iterate through the range:

For each number in the range **[left, right]**, check if it is a self-dividing number by using the helper function checkDigit().
If the number is self-dividing, add it to the result list.
Return the result list.

Solution Code
```cpp
class Solution {
public:
    // Helper function to check if a number is self-dividing
    bool checkDigit(int num) {
        int original = num;  // Preserve original value to use for modulus check
        while (num > 0) {
            int digit = num % 10;
            // Check if the digit is zero or if num is not divisible by the digit
            if (digit == 0 || original % digit != 0) {
                return false;
            }
            num /= 10;
        }
        return true;
    }

    // Main function to find all self-dividing numbers in the range [left, right]
    vector<int> selfDividingNumbers(int left, int right) {
        vector<int> ans;

        // Iterate through all numbers in the range [left, right]
        for (int i = left; i <= right; i++) {
            if (checkDigit(i)) {
                ans.push_back(i);  // Add self-dividing number to the result list
            }
        }

        return ans;
    }
};

```
## Explanation
checkDigit() function:
This function takes an integer num and checks if it is a self-dividing number. It works as follows:

1. It stores the original value of num in original.
2. It then loops through each digit of num. If a digit is 0, the number is not self-dividing, and the function returns false.
3. If the digit divides the number without a remainder, it proceeds to check the next digit.
4. If all digits divide the number, it returns true, indicating the number is self-dividing.
selfDividingNumbers() function:
This function iterates through each number in the range [left, right] and calls the checkDigit() function to verify if it's a self-dividing number. If it is, it adds the number to the result vector ans. After iterating through the entire range, the function returns the list of self-dividing numbers.

## Time Complexity
The time complexity of the checkDigit() function is O(d), where d is the number of digits in the number num.
The selfDividingNumbers() function iterates through all numbers in the range [left, right], making the overall time complexity O(n * d), where n is the size of the range and d is the average number of digits in the numbers in the range.
Thus, the time complexity is linear with respect to the number of numbers in the range and the number of digits in each number.

Example Walkthrough
## Example 1
```
Input:
left = 1, right = 22
```
Execution:
The function iterates from 1 to 22.
The self-dividing numbers in this range are: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22].

```
Output:
[1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
```
## Example 2
```
Input:
left = 47, right = 85
```
Execution:
The function iterates from 47 to 85.
The self-dividing numbers in this range are: [48, 55, 66, 77].
```
Output:
[48, 55, 66, 77]
```




