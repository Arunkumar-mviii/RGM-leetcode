# LeetCode Solutions - Day 3

---

## 1. **[7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)**

### Problem Description

Given a 32-bit signed integer `x`, reverse the digits of `x`. If reversing the integer causes overflow, return 0.

### Solution

```cpp
int reverse(int x) {
    long rev = 0;
    while (x != 0) {
        rev = rev * 10 + x % 10;
        x /= 10;
    }
    if (rev > INT_MAX || rev < INT_MIN) {
        return 0;
    }
    return rev;
}
```

### Explanation

- We reverse the digits by repeatedly extracting the last digit using `x % 10`, adding it to the reversed number `rev`, and reducing `x` by dividing it by 10.
- We check for overflow by comparing `rev` with `INT_MAX` and `INT_MIN`.

---

## 2. **[7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)** (Alternate Approach)

### Problem Description

Same as the previous problem.

### Solution

```cpp
int reverse(int x) {
    int rev = 0;
    while (x) {
        if (rev > 214748364 || rev < -214748364) return 0;
        rev = rev * 10 + x % 10;
        x /= 10;
    }
    return rev;
}
```

### Explanation

- This approach uses a simpler comparison for overflow (with `214748364`), which ensures the reversed number remains within the 32-bit signed integer range.
- The logic for reversing the digits is the same as the first solution.

---

## 3. **[9. Palindrome Number](https://leetcode.com/problems/palindrome-number/)**

### Problem Description

Determine whether an integer is a palindrome. An integer is a palindrome if it reads the same backward as forward.

### Solution

```cpp
bool isPalindrome(int x) {
    if (x < 0 || (x % 10 == 0 && x != 0)) return false;
    int rev = 0;
    while (x > rev) {
        rev = rev * 10 + x % 10;
        x /= 10;
    }
    return x == rev || x == rev / 10;
}
```

### Explanation

- Negative numbers and numbers ending with 0 (except 0) are automatically not palindromes.
- We reverse the second half of the number and compare it with the first half.

---

## 4. **[509. Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)**

### Problem Description

Given an integer `N`, return the `N`-th number in the Fibonacci sequence.

### Solution

```cpp
int fib(int N) {
    if (N <= 1) {
        return N;
    }

    int current = 0;
    int prev1 = 1;
    int prev2 = 0;

    for (int i = 2; i <= N; i++) {
        current = prev1 + prev2;
        prev2 = prev1;
        prev1 = current;
    }
    return current;
}
```

### Explanation

- This solution uses an iterative approach to calculate the Fibonacci number.
- We keep track of the last two Fibonacci numbers (`prev1` and `prev2`) and update them at each step.

---

## 5. **[1137. N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/)**

### Problem Description

The Tribonacci sequence is similar to the Fibonacci sequence, except that the first three numbers are 0, 1, 1. Given an integer `n`, return the `n`-th Tribonacci number.

### Solution

```cpp
int tribonacci(int n) {
    if (n == 0) return 0;
    if (n <= 2) return 1;
    int a = 0, b = 1, c = 1, current;
    for (int i = 3; i <= n; i++) {
        current = a + b + c;
        a = b;
        b = c;
        c = current;
    }
    return c;
}
```

### Explanation

- The first three Tribonacci numbers are `0`, `1`, `1`. We iterate and calculate the subsequent numbers by summing the last three numbers.

---

## 6. **[1281. Subtract the Product and Sum of Digits of an Integer](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/)**

### Problem Description

Given an integer `n`, return the difference between the product and the sum of its digits.

### Solution

```cpp
int subtractProductAndSum(int n) {
    int product = 1;
    int sum = 0;

    while (n > 0) {
        int digit = n % 10;   
        product *= digit;     
        sum += digit;        
        n /= 10;               
    }
    return product - sum;
}
```

### Explanation

- We extract each digit of `n` using `n % 10`, update the `product` and `sum` accordingly, and reduce `n` by dividing it by 10.
- Finally, we return the difference between the product and sum of the digits.

---

## 7. **[1342. Number of Steps to Reduce a Number to Zero](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/)**

### Problem Description

Given an integer `num`, return the number of steps required to reduce it to zero. In each step, if `num` is even, divide it by 2. If `num` is odd, subtract 1 from it.

### Solution

```cpp
int numberOfSteps(int num) {
    int steps = 0;
    while (num) {
        num = num % 2 ? num - 1 : num / 2;
        steps++;
    }
    return steps;
}
```

### Explanation

- We check if the number is even or odd.
- If it is odd, we subtract 1. If it is even, we divide it by 2.
- We count how many steps it takes to reduce `num` to zero.

---
