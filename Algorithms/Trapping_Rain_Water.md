# Trapping Rain Water

## Problem Description

Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.

### Example:

**Input:**  
`height = [0,1,0,2,1,0,1,3,2,1,2,1]`

**Output:**  
`6`

**Explanation:**  
The above elevation map (black section) is represented by the array `[0,1,0,2,1,0,1,3,2,1,2,1]`. In this case, 6 units of rainwater (blue section) are being trapped.

---

**Input:**  
`height = [4,2,0,3,2,5]`

**Output:**  
`9`

---

## Approach

The problem can be solved using the **Two Pointer Approach**. The basic idea is to maintain two pointers, one at the beginning (`left`) and one at the end (`right`) of the elevation map. 

1. We maintain two variables: `leftBar` and `rightBar` to store the maximum heights encountered from the left and right sides, respectively.
2. We then iterate through the array, comparing the heights at the `left` and `right` pointers.
3. If `leftBar` is smaller, we calculate the water trapped at the `left` pointer and move the `left` pointer to the right.
4. If `rightBar` is smaller, we calculate the water trapped at the `right` pointer and move the `right` pointer to the left.
5. The process continues until the `left` pointer meets the `right` pointer, and the total water trapped is calculated.

### Code Implementation:

```cpp
class Solution {
public:
    int trap(vector<int>& arr) {
         
        int n = arr.size();
        int ans = 0;
        int leftBar = arr[0];
        int rightBar = arr[n - 1];
        int left = 0;
        int right = n - 1;
        
        while (left < right) {
            
            if (leftBar < rightBar) {
                // If current left height is less, move the left pointer
                if (arr[left] > leftBar)
                    leftBar = arr[left];  // Update the leftBar
                else
                    ans += leftBar - arr[left++];  // Calculate water and move left pointer
            }
            else {
                // If current right height is less, move the right pointer
                if (arr[right] > rightBar)
                    rightBar = arr[right];  // Update the rightBar
                else
                    ans += rightBar - arr[right--];  // Calculate water and move right pointer
            }
        }
        return ans;  // Return the total amount of trapped water
    }
};

```

# Example Walkthrough:
## Example 1:
**Input**
`height = [0,1,0,2,1,0,1,3,2,1,2,1]`

1. The maximum height from the left is calculated progressively for each position.
2. The maximum height from the right is calculated similarly.
3. Water is trapped at the positions where the height is less than the maximum heights on both sides.
**Output**
`6`

## Example 2:
**Input:**  
`height = [4,2,0,3,2,5]`

Water is trapped between the bars at indices 1, 2, 3, and 4.
Output:
`9`
