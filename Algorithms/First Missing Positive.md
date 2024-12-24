# First Missing Positive

## Problem Description

Given an unsorted integer array `nums`, return the smallest positive integer that is not present in the array.

### Constraints:
- You must implement an algorithm that runs in **O(n)** time and uses **O(1)** auxiliary space.

### Example:

**Input:**  
`nums = [1, 2, 0]`

**Output:**  
`3`

**Input:**  
`nums = [3, 4, -1, 1]`

**Output:**  
`2`

**Input:**  
`nums = [7, 8, 9, 11, 12]`

**Output:**  
`1`

## Optimized Solution

### Intuition

We need to place the elements in their respective positions (i.e., element `x` should be at index `x - 1`). After rearranging, the smallest missing positive integer will be the first index where the element doesn't match the index value.

### Steps:

1. **Rearrange the array**: Place each element `x` in the index `x - 1` if `x` is between `1` and `n` (inclusive). Ignore elements outside this range.
2. **Find the missing positive number**: After rearranging, the first index where the value isn't `i + 1` will give us the missing number.
3. **Edge case**: If all elements are correctly placed, the smallest missing positive number is `n + 1`.

## Code Implementation

```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int n = nums.size();

        // Step 1: Rearrange elements to their correct positions
        for (int i = 0; i < n; i++) {
            int element = nums[i];
            // Check if the element is within the valid range [1, n]
            if (element >= 1 && element <= n) {
                int correctPos = element - 1;  // correct index for the element
                // If the element is not already in its correct position
                if (nums[correctPos] != element) {
                    swap(nums[i], nums[correctPos]);
                    i--;  // Check the swapped element again
                }
            }
        }

        // Step 2: Find the first index where the element is not i + 1
        for (int i = 0; i < n; i++) {
            if (nums[i] != i + 1) {
                return i + 1;
            }
        }

        // Step 3: If all elements are in their correct positions, return n + 1
        return n + 1;
    }
};
```

## Time and Space Complexity:

- **Time Complexity**:  
  - Rearranging the elements takes **O(n)** time, as we traverse the array once.
  - Checking the missing element takes another **O(n)** time.  
  Thus, the total time complexity is **O(n)**.

- **Space Complexity**:  
  - We are using the array in-place without any extra space, so the space complexity is **O(1)**.
