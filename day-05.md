
# LeetCode Solutions - Day 5

---

## 1. **[441. Arranging Coins](https://leetcode.com/problems/arranging-coins/)**

### Problem Description

You have `n` coins. You want to build a staircase with these coins. The staircase consists of `k` rows where the first row has 1 coin, the second row has 2 coins, the third row has 3 coins, and so on. Return the total number of complete rows of the staircase.

### Solution

```cpp
int arrangeCoins(int n) {
    int rows = 0;
    while (n >= rows + 1) {
        rows++;
        n -= rows;
    }
    return rows;
}
```

### Explanation

- We keep adding rows until we run out of coins to fill the next row.
- The condition `n >= rows + 1` ensures that we can add a new row.
- After the loop, the `rows` variable contains the number of complete rows.

---

## 2. **[507. Perfect Number](https://leetcode.com/problems/perfect-number/)**

### Problem Description

A perfect number is a positive integer that is equal to the sum of its proper divisors, excluding the number itself. Return `true` if the number is perfect, otherwise return `false`.

### Solution

```cpp
bool checkPerfectNumber(int num) {
    int sum = 0;
    for (int i = 1; i <= num / 2; i++) {
        if (num % i == 0) {
            sum += i;
        }
    }
    return sum == num;
}
```

### Explanation

- We calculate the sum of divisors of `num` by iterating from `1` to `num / 2`.
- If the sum of divisors equals the number itself, it is a perfect number.

---

## 3. **[172. Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/)**

### Problem Description

Given an integer `n`, return the number of trailing zeroes in `n!` (factorial of `n`).

### Solution

```cpp
int trailingZeroes(int n) {
    int zeroCount = 0;
    while (n > 0) {
        n /= 5;
        zeroCount += n;
    }
    return zeroCount;
}
```

### Explanation

- The number of trailing zeros in a factorial is determined by how many times 5 appears as a factor in the numbers from `1` to `n`. This is because every pair of 2 and 5 contributes a trailing zero.
- We repeatedly divide `n` by `5` to count how many multiples of 5 are there in the range `1` to `n`.

---

## 4. **[3099. Harshad Number](https://leetcode.com/problems/harshad-number/)**

### Problem Description

Given an integer `x`, return the sum of its digits if `x` is divisible by the sum of its digits. Otherwise, return `-1`.

### Solution

```cpp
int sumOfTheDigitsOfHarshadNumber(int x) {
    int digitSum = 0;
    int temp = x;
    while (temp > 0) {
        digitSum += temp % 10;
        temp /= 10;
    }
    if (x % digitSum == 0) {
        return digitSum;
    }
    return -1;
}
```

### Explanation

- We calculate the sum of digits of `x`.
- If `x` is divisible by the sum of its digits, we return the sum; otherwise, we return `-1`.

---

## 5. **[1518. Water Bottles](https://leetcode.com/problems/water-bottles/)**

### Problem Description

There are `numBottles` full water bottles and `numExchange` empty bottles. You can exchange an empty bottle for a full one, and after drinking it, the bottle becomes empty again. Calculate how many full water bottles you can drink.

### Solution

```cpp
int numWaterBottles(int numBottles, int numExchange) {
    int res = 0;
    int empty = 0;
    while(numBottles) {
        res += numBottles;
        empty += numBottles;
        numBottles = empty / numExchange;
        empty = empty % numExchange;
    }
    return res;
}
```

### Explanation

- We calculate how many bottles can be drunk by repeatedly exchanging empty bottles for full ones until we run out of bottles to exchange.
- The variable `res` stores the total number of bottles drunk, and `empty` keeps track of how many empty bottles we have after each exchange.

---

## 6. **[2520. Count the Digits That Divide a Number](https://leetcode.com/problems/count-the-digits-that-divide-a-number/)**

### Problem Description

Given an integer `num`, return the number of digits that divide `num` evenly.

### Solution

```cpp
int countDigits(int num) {
    int originalNum = num;
    int count = 0;
    while (num > 0) {
        int digit = num % 10;
        if (digit != 0 && originalNum % digit == 0) {
            count++;
        }
        num /= 10;
    }
    return count;
}
```

### Explanation

- We iterate through each digit of `num` and check if it divides `num` evenly.
- We increment the `count` variable each time a digit divides `num`.

---

## 7. **[2591. Distribute Money to Maximum Children](https://leetcode.com/problems/distribute-money-to-maximum-children/)**

### Problem Description

You are given `money` and `children`. You have to distribute the money to the children such that each child gets at least 1 dollar. The goal is to maximize the number of children who receive exactly 7 dollars.

### Solution

```cpp
int distMoney(int money, int children) {
    if (money < children) return -1;
    if (money < 8) return 0;
    money -= children;
    int count = 0;
    while (true) {
        if (!children) {
            if (!money) return count;
            return count - 1;
        }
        if (children != 0 && money >= 7) {
            if ((money - 7) != 3) {
                children--;
                money -= 7;
                count++;
            } else if ((money - 7) == 3 && children > 2) {
                children--;
                money -= 7;
                count++;
            } else {
                return count;
            }
        } else {
            return count;
        }
    }
    return -1;
}
```

### Explanation

- We distribute the money as much as possible while making sure each child gets at least one dollar.
- We try to maximize the number of children who get 7 dollars, adjusting as needed based on the remaining money.

---
