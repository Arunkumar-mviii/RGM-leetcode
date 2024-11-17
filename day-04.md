# LeetCode Solutions - Day 4

---

## 1. **[1952. Three Divisors](https://leetcode.com/problems/three-divisors/)**

### Problem Description

Given an integer `n`, return `true` if `n` has exactly three divisors. Otherwise, return `false`.

### Solution

```cpp
bool isThree(int n) {
    int count = 0;
    for (int i = 1; i <= n; i++) {
        if (n % i == 0) count++;
    }
    return (count == 3) ? 1 : 0;
}
```

### Explanation

- The solution iterates through all integers from `1` to `n`, counting how many divisors `n` has.
- If there are exactly 3 divisors, it returns `true`; otherwise, it returns `false`.

---

## 2. **[2427. Number of Common Factors](https://leetcode.com/problems/number-of-common-factors/)**

### Problem Description

Given two integers `a` and `b`, return the number of common factors between them.

### Solution

```cpp
int commonFactors(int a, int b) {
    int count = 0;
    int n = fmin(a, b);
    for (int i = 1; i <= n; i++) {
        if (a % i == 0 && b % i == 0) count++;
    }
    return count;
}
```

### Explanation

- We calculate the minimum of `a` and `b` to avoid unnecessary checks.
- We iterate from `1` to the minimum value and check if both numbers are divisible by `i`.
- We count how many common divisors they have.

---

## 3. **[2652. Sum Multiples](https://leetcode.com/problems/sum-multiples/)**

### Problem Description

Given an integer `n`, return the sum of all numbers less than or equal to `n` that are divisible by `3`, `5`, or `7`.

### Solution

```cpp
int sumOfMultiples(int n) {
    int sum = 0;
    for (int i = 1; i <= n; i++) {
        if (i % 3 == 0 || i % 5 == 0 || i % 7 == 0) {
            sum += i;
        }
    }
    return sum;
}
```

### Explanation

- We iterate through all numbers from `1` to `n`.
- If a number is divisible by `3`, `5`, or `7`, we add it to the sum.
- Finally, we return the sum.

---

## 4. **[2739. Total Distance Traveled](https://leetcode.com/problems/total-distance-traveled/)**

### Problem Description

Given two integers `mainTank` and `additionalTank`, calculate the total distance that can be traveled with the fuel provided. The car uses 5 liters of fuel to travel 50 kilometers, and the extra tank adds 1 liter to the main tank in each refill.

### Solution

```cpp
int distanceTraveled(int mainTank, int additionalTank) {
    int totalDistance = 0;
    while (mainTank > 0) {
        if (mainTank >= 5) {
            mainTank -= 5;
            totalDistance += 50;
            if (additionalTank > 0) {
                mainTank += 1;
                additionalTank -= 1;
            }
        } else {
            totalDistance += mainTank * 10;
            mainTank = 0;
        }
    }
    return totalDistance;
}
```

### Explanation

- We use a loop to calculate the total distance traveled.
- For every 5 liters in the main tank, the car can travel 50 kilometers.
- We keep refilling from the additional tank if available.
- If the remaining fuel is less than 5 liters, we calculate the remaining distance proportionally.

---

## 5. **[263. Ugly Number](https://leetcode.com/problems/ugly-number/)**

### Problem Description

Determine if a number `n` is an ugly number. Ugly numbers are positive numbers whose prime factors only include `2`, `3`, and `5`.

### Solution

```cpp
bool isUgly(int n) {
    if (n < 1) return false;
    while (n % 2 == 0 || n % 3 == 0 || n % 5 == 0) {
        if (n % 2 == 0) n /= 2;
        if (n % 3 == 0) n /= 3;
        if (n % 5 == 0) n /= 5;
    }
    return n == 1;
}
```

### Explanation

- If `n` is less than 1, it is not an ugly number.
- We divide `n` by `2`, `3`, and `5` as long as it is divisible by these numbers.
- If the result is 1, the number is an ugly number.

---

## 6. **[202. Happy Number](https://leetcode.com/problems/happy-number/)**

### Problem Description

Write an algorithm to determine if a number `n` is happy. A happy number is defined by the following process:

1. Starting with any positive integer, replace the number by the sum of the squares of its digits.
2. Repeat the process until the number equals 1 or loops endlessly in a cycle that does not include 1.

### Solution

```cpp
int getNext(int n) {
    int totalSum = 0;
    while (n > 0) {
        int d = n % 10;
        n = n / 10;
        totalSum += d * d;
    }
    return totalSum;
}

bool isHappy(int n) {
    int slowRunner = n;
    int fastRunner = getNext(n);
    while (fastRunner != 1 && slowRunner != fastRunner) {
        slowRunner = getNext(slowRunner);
        fastRunner = getNext(getNext(fastRunner));
    }
    return fastRunner == 1;
}
```

### Explanation

- We calculate the sum of the squares of the digits of `n` in a helper function `getNext()`.
- We use the Floyd's cycle detection algorithm (slow and fast runners) to detect if the process ends at 1 or falls into a cycle.

---

## 7. **[231. Power of Two](https://leetcode.com/problems/power-of-two/)**

### Problem Description

Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`.

### Solution

```cpp
bool isPowerOfTwo(int n) {
    if (n == 0) return false;
    while (n % 2 == 0) n /= 2;
    return n == 1;
}
```

### Explanation

- We divide `n` by `2` as long as it is divisible by `2`.
- If the final result is 1, `n` is a power of two.

---

## 8. **[326. Power of Three](https://leetcode.com/problems/power-of-three/)**

### Problem Description

Given an integer `n`, return `true` if it is a power of three. Otherwise, return `false`.

### Solution

```cpp
bool isPowerOfThree(int n) {
    if (n < 1) return false;
    if (n == 1) return true;
    while (n % 3 == 0) n /= 3;
    return n == 1;
}
```

### Explanation

- We divide `n` by `3` as long as it is divisible by `3`.
- If the final result is 1, `n` is a power of three.

---
