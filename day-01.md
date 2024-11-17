# LeetCode Solutions - Day 1

---

## 1. **[2235. Add Two Integers](https://leetcode.com/problems/add-two-integers/)**

### Problem Description

Given two integers `num1` and `num2`, return the sum of the two numbers.

### Solution

```cpp
int sum(int num1, int num2) {
    return num1 + num2;
}
```

### Explanation

This is a simple addition problem where we directly return the sum of `num1` and `num2`.

---

## 2. **[2119. A Number After a Double Reversal](https://leetcode.com/problems/a-number-after-a-double-reversal/)**

### Problem Description

Reversing an integer twice results in the same number. If the number has a trailing zero, then after the first reversal, the trailing zeros will be removed. The problem asks to check if the number is the same after performing the double reversal.

### Solution

```cpp
bool isSameAfterReversals(int x) {
    return x == 0 || (x % 10 != 0);
}
```

### Explanation

The number will only be different after double reversal if it ends with a zero. If `x` ends with a non-zero digit, the number remains unchanged after both reversals.

---

## 3. **[2481. Minimum Cuts to Divide a Circle](https://leetcode.com/problems/minimum-cuts-to-divide-a-circle/)**

### Problem Description

A circle can be divided into `n` equal parts using cuts. The problem asks how many cuts are required to divide the circle into `n` equal parts.

### Solution

```cpp
int numberOfCuts(int n) {
    return (n == 1) ? 0 : (n % 2 == 0) ? n / 2 : n;
}
```

### Explanation

- If `n = 1`, no cuts are needed.
- If `n` is even, the number of cuts required is `n / 2`.
- If `n` is odd, the number of cuts required is equal to `n`.

---

## 4. **[1025. Divisor Game](https://leetcode.com/problems/divisor-game/)**

### Problem Description

In this game, a player starts with `n` and in each turn, they must subtract a divisor of `n` (other than `n` itself) to make `n` smaller. The player who cannot make a move loses. The task is to determine if the first player will win.

### Solution

```cpp
bool divisorGame(int n) {
    return n % 2 == 0;
}
```

### Explanation

If `n` is even, the first player will always win by choosing `1` as the divisor. If `n` is odd, the first player will lose.

---

## 5. **[292. Nim Game](https://leetcode.com/problems/nim-game/)**

### Problem Description

The Nim Game is played with a pile of `n` stones. In each move, a player must take 1, 2, or 3 stones from the pile. The player who cannot take any stones loses. The task is to determine whether the first player will win given `n` stones.

### Solution

```cpp
bool canWinNim(int n) {
    return (n % 4 != 0);
}
```

### Explanation

The game has a periodic pattern where if `n % 4 == 0`, the second player can always win. Otherwise, the first player has a winning strategy.

---

## 6. **[258. Add Digits](https://leetcode.com/problems/add-digits/)**

### Problem Description

Given a non-negative integer `num`, repeatedly add all its digits until the result has only one digit.

### Solution

```cpp
int addDigits(int num) {
    return num == 0 ? 0 : 1 + (num - 1) % 9;
}
```

### Explanation

This is based on the digital root concept, where a number can be reduced to a single digit by summing its digits repeatedly. The result is `1 + (num - 1) % 9` for any number except `0`.

---

## 7. **[1688. Count of Matches in Tournament](https://leetcode.com/problems/count-of-matches-in-tournament/)**

### Problem Description

In a tournament, there are `n` teams. In each match, one team is eliminated. The task is to determine the number of matches that must be played to determine a winner.

### Solution

```cpp
int numberOfMatches(int n) {
    return n - 1;
}
```

### Explanation

Each match eliminates one team, so the number of matches required to determine a winner is always `n - 1` (where `n` is the number of teams).

---

## 8. **[2413. Smallest Even Multiple](https://leetcode.com/problems/smallest-even-multiple/)**

### Problem Description

Given a positive integer `n`, return the smallest positive integer that is a multiple of both `n` and `2`.

### Solution

```cpp
int smallestEvenMultiple(int n) {
    return (n % 2 == 0) ? n : n * 2;
}
```

### Explanation

If `n` is already even, then the smallest multiple of `n` and `2` is `n` itself. Otherwise, the smallest multiple is `n * 2`.
