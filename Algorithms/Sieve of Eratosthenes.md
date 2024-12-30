# Count Primes Less Than n

## Problem Description

Given an integer `n`, return the number of prime numbers that are strictly less than `n`.

### Example:

**Input:**  
`n = 10`

**Output:**  
`4`

**Explanation:**  
There are 4 prime numbers less than 10:   `2`, `3`, `5`, `7`.

---

**Input:**  
`n = 0`

**Output:**  
`0`

---

**Input:**  
`n = 1`

**Output:**  
`0`

---

## Approach

The problem can be solved using the **Sieve of Eratosthenes** algorithm, which is an efficient way to find all prime numbers less than `n`. The main idea behind this approach is to mark all multiples of each prime number starting from `2` as non-prime. Here's how the approach works:

1. **Initialize a boolean array `primes`** of size `n`, where each index represents whether the number is prime. Initially, all numbers are assumed to be prime (marked as `1`).
2. **Iterate through the numbers starting from `2`**, and for each number `i`, mark all of its multiples as non-prime (set them to `0`).
3. **Count the prime numbers** by checking how many numbers are still marked as `1` (prime) from `2` to `n-1`.

### Code Implementation:

```cpp
class Solution {
public:
    int countPrimes(int n) {
        vector<int> primes(n, 1); // Initialize the prime array with 1, meaning all are initially prime

        for(int i = 2; i < n; i++) {
            if(primes[i] == 1) { // If i is prime
                for(int j = i * i; j < n; j += i) { // Mark all multiples of i as non-prime
                    if(primes[j] == 1) {
                        primes[j] = 0; // Mark multiples as non-prime
                    }
                }
            }
        }

        // Count how many numbers are still marked as prime
        int count = 0;
        for(int i = 2; i < n; i++) {
            if(primes[i] == 1) count++;
        }

        return count;
    }
};
