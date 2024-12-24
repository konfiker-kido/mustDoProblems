# Search in a Strictly Sorted 2D Matrix

Given a strictly sorted 2D matrix `mat[][]` of size `n x m` and a number `x`, determine whether the number `x` exists in the matrix.

## Properties of the Strictly Sorted Matrix:
1. Each row is sorted in **strictly increasing order**.
2. The first element of the `i-th` row (where `i > 0`) is **greater than the last element** of the `(i-1)-th` row.

---

## Problem Examples

### Example 1
**Input:**
```
mat[][] = [[1, 5, 9], 
           [14, 20, 21], 
           [30, 34, 43]], 
x = 14
```

**Output:**
```
true
```

**Explanation:**  
The number `14` is present in the matrix.

---

### Example 2
**Input:**
```
mat[][] = [[1, 5, 9, 11], 
           [14, 20, 21, 26], 
           [30, 34, 43, 50]], 
x = 42
```

**Output:**
```
false
```

**Explanation:**  
The number `42` is not present in the matrix.

---

### Example 3
**Input:**
```
mat[][] = [[87, 96, 99], 
           [101, 103, 111]], 
x = 101
```

**Output:**
```
true
```

**Explanation:**  
The number `101` is present in the matrix.

---

## Efficient Solution

We can efficiently search the matrix using the following approach:
1. Start at the **top-right corner** of the matrix.
2. If the current element is greater than `x`, move **left**.
3. If the current element is less than `x`, move **down**.
4. If you find `x`, return `true`.
5. If you reach out of bounds, return `false`.

---

### Code Implementation

```cpp


// Function to search for a number in a strictly sorted matrix
bool searchMatrix(vector<vector<int>> &mat, int x) {
    int n = mat.size(); // Number of rows
    int m = mat[0].size(); // Number of columns
    int i = 0, j = m - 1; // Start from the top-right corner

    while (i < n && j >= 0) {
        if (mat[i][j] > x) {
            j--; // Move left
        } else if (mat[i][j] < x) {
            i++; // Move down
        } else {
            return true; // Found the element
        }
    }
    return false; // Element not found
}
```

---

## Explanation of the Code

1. **Initialization**:
   - `i = 0, j = m - 1`: Start at the top-right corner of the matrix.
   - Traverse rows (`i`) and columns (`j`) based on conditions.

2. **Loop**:
   - If the current element is greater than `x`, decrement `j` to move left.
   - If the current element is less than `x`, increment `i` to move down.
   - If the current element equals `x`, return `true`.

3. **Termination**:
   - If `i >= n` or `j < 0`, the element does not exist in the matrix.

---

## Complexity Analysis

- **Time Complexity**: \( O(n + m) \)
  - At most, we make \( n + m \) moves through the matrix.
- **Space Complexity**: \( O(1) \)
  - No extra space is used.

---

