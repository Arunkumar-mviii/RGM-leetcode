
# LeetCode Solutions - Day 6

---

## 1. **[1523. Count Odd Numbers in an Interval Range](https://leetcode.com/problems/count-odd-numbers-in-an-interval-range/)**

### Problem Description

Given two integers `low` and `high`, return the count of odd numbers between them, inclusive.

### Solution

```cpp
int countOdds(int low, int high) {
    if((low & 1) == 0) low++; // If low is even, make it odd
    return low > high ? 0 : (high - low) / 2 + 1; 
}
```

### Explanation

- If `low` is even, we increment it to make it odd.
- We then check if the range `low` to `high` is valid, and count the number of odd numbers by dividing the range by 2 and adding 1 if necessary.

---

## 2. **[231. Power of Two](https://leetcode.com/problems/power-of-two/)**

### Problem Description

Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`.

### Solution

```cpp
bool isPowerOfTwo(int x) {
    long n = x;
    if (n && (n & (n - 1)) == 0)  // Check if only one bit is set
        return true;
    else 
        return false;
}
```

### Explanation

- A number is a power of two if it has only one bit set to `1` in its binary representation. The expression `(n & (n - 1)) == 0` checks this condition.

---

## 3. **[342. Power of Four](https://leetcode.com/problems/power-of-four/)**

### Problem Description

Given an integer `n`, return `true` if it is a power of four. Otherwise, return `false`.

### Solution

```cpp
int isPowerOfFour(int n) {
    if (n > 0 && (n & (n - 1)) == 0 && (n % 3 == 1))  // Must be power of 2 and n % 3 == 1 for powers of 4
        return 1;
    return 0;
}
```

### Explanation

- A number is a power of four if:
  1. It is a power of two: `(n & (n - 1)) == 0`
  2. The number modulo 3 is equal to 1, because all powers of four modulo 3 are 1.
  
---

## 4. **[191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)**

### Problem Description

Write a function that returns the number of `1` bits in an integer.

### Solution

```cpp
int hammingWeight(int n) {
    int sum = 0;
    while (n != 0) {
        sum++;
        n = n & (n - 1);  // This removes the rightmost 1 bit
    }
    return sum;
}
```

### Explanation

- The `n = n & (n - 1)` operation removes the rightmost `1` bit in the number.
- We repeatedly apply this operation and count how many `1` bits are present.

---

## 5. **[461. Hamming Distance](https://leetcode.com/problems/hamming-distance/)**

### Problem Description

The Hamming distance between two integers is the number of positions at which the corresponding bits are different. Write a function to compute the Hamming distance.

### Solution

```cpp
int hammingDistance(int x, int y) {
    int xor_val = x ^ y;  // XOR of x and y will set 1 at positions where x and y differ
    int distance = 0;
    while (xor_val != 0) {
        distance += 1;
        xor_val = xor_val & (xor_val - 1);  // This removes the rightmost 1 bit
    }
    return distance;
}
```

### Explanation

- The XOR operation `x ^ y` sets the bits to `1` where `x` and `y` differ.
- We then count the number of `1` bits in the result using the same technique as in **Hamming Weight**.

---

## 6. **[693. Binary Number with Alternating Bits](https://leetcode.com/problems/binary-number-with-alternating-bits/)**

### Problem Description

Given an integer `n`, return `true` if the binary representation of `n` has alternating bits (e.g., `010101` or `101010`), and `false` otherwise.

### Solution

```cpp
bool hasAlternatingBits(int n) {
    return (n & (n >> 1)) == 0 && (n & (n >> 2)) == (n >> 2);  // Check if adjacent bits differ
}
```

### Explanation

- The expression `(n & (n >> 1)) == 0` checks if adjacent bits differ (no two consecutive bits are the same).
- Additionally, `(n & (n >> 2)) == (n >> 2)` ensures that there is no pattern of repeating bits every two places.

---
