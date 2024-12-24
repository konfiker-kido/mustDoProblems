# First and Last Occurrences

## Problem Description

Given a sorted array `arr` containing `n` elements with possibly some duplicates, the task is to find the first and last occurrences of an element `x` in the given array.  
If the number `x` is not found in the array, then return both the indices as `-1`.

### Example:

**Input:**  
`n = 9`, `x = 5`  
`arr[] = { 1, 3, 5, 5, 5, 5, 67, 123, 125 }`

**Output:**  
`2 5`

**Explanation:**  
The first occurrence of `5` is at index `2` and the last occurrence of `5` is at index `5`.

---

**Input:**  
`n = 9`, `x = 7`  
`arr[] = { 1, 3, 5, 5, 5, 5, 7, 123, 125 }`

**Output:**  
`6 6`

**Explanation:**  
The first and last occurrence of `7` is at index `6`.

---

## Approach

We can solve this problem in two different ways:

1. **Naive Approach (O(N)):**  
   Use two pointers to traverse the array, one starting from the left and the other from the right, and search for the first and last occurrences of `x`.

2. **Optimized Approach (O(log N)):**  
   Use binary search to find the first and last occurrences of `x`. Since the array is sorted, binary search will help us find the indices in logarithmic time.

### Naive Approach (O(N)) - Using Two Pointers

```cpp
class Solution {
public:
    vector<int> find(int arr[], int n, int x) {
        int s = 0, e = n - 1;
        while (s <= e) {
            if (arr[s] == x && arr[e] == x) return {s, e};
            if (arr[s] != x) s++;
            if (arr[e] != x) e--;
        }
        return {-1, -1};
    }
};
```
## Explanation:
1. We use two pointers, s starting from the left and e starting from the right of the array.
2. We check if both arr[s] and arr[e] are equal to x, in which case we return their indices.
3. If arr[s] is not x, we increment s. If arr[e] is not x, we decrement e.
4. This approach checks both the left and right ends to find the first and last occurrence of x.


### Optimized Approach (O(log N)) - Using Binary Search
```cpp
class Solution {
public:
    vector<int> find(int arr[], int n, int x) {
        int s = 0, e = n - 1;
        int first = -1, second = -1;
        int mid = s + (e - s) / 2;

        // Finding the first occurrence
        while (s <= e) {
            if (arr[mid] == x) {
                e = mid - 1;
                first = mid;
            } else if (arr[mid] > x) {
                e = mid - 1;
            } else {
                s = mid + 1;
            }
            mid = s + (e - s) / 2;
        }

        // If the element is not found
        if (first == -1) return {-1, -1};

        // Reset pointers for the second part
        s = 0, e = n - 1, mid = s + (e - s) / 2;

        // Finding the last occurrence
        while (s <= e) {
            if (arr[mid] == x) {
                s = mid + 1;
                second = mid;
            } else if (arr[mid] > x) {
                e = mid - 1;
            } else {
                s = mid + 1;
            }
            mid = s + (e - s) / 2;
        }

        return {first, second};
    }
};



```
---
## Explanation:
### First Occurrence:
1. We perform binary search to find the first occurrence of x. If arr[mid] equals x, we continue searching on the left part (e = mid - 1) to ensure we find the leftmost occurrence. The first variable stores the index.

### Second Occurrence:
1. After finding the first occurrence, we reset the pointers and perform a second binary search to find the last occurrence of x. If arr[mid] equals x, we continue searching on the right part (s = mid + 1) to ensure we find the rightmost occurrence. The second variable stores the index.


## Time Complexity:
The time complexity is O(log N) due to the binary search for both the first and last occurrences.

## Space Complexity:
The space complexity is O(1), as no extra space is used apart from a few variables.





