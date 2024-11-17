
# LeetCode Solutions - Day 8

---

## 1. **[136. Single Number](https://leetcode.com/problems/single-number/)**

### Problem Description

Given an array `nums` where every element appears twice except for one, find that single one. You must implement a solution with a linear runtime complexity.

### Solution

```cpp
int singleNumber(int* a, int n) {
    int res = 0;
    for(int i = 0; i < n; i++) {
        res = res ^ a[i];
    }
    return res;
}
```

### Explanation

- The XOR operation `^` cancels out pairs of equal numbers (because `a ^ a = 0`).
- We apply this operation to all elements in the array. The result will be the single number that does not have a pair.

---

## 2. **[268. Missing Number](https://leetcode.com/problems/missing-number/)**

### Problem Description

Given an array `nums` containing `n` distinct numbers taken from the range `0` to `n`, find the one number that is missing from the array.

### Solution 1 (XOR approach)

```cpp
int missingNumber(int* nums, int n) {
    int missing = n;
    for (int i = 0; i < n; i++) {
        missing ^= i ^ nums[i];
    }
    return missing;
}
```

### Explanation

- Using XOR, we cancel out all the numbers that appear in both the range `0` to `n-1` and the array `nums`.
- The result will be the missing number.

### Solution 2 (Sum approach)

```cpp
int missingNumber(int* nums, int n) {
    int sum = n * (n + 1) / 2;  // Sum of numbers from 0 to n
    for (int i = 0; i < n; i++) {
        sum -= nums[i];  // Subtract the sum of numbers present in the array
    }
    return sum;
}
```

### Explanation

- The sum of all numbers from `0` to `n` is calculated using the formula `n * (n + 1) / 2`.
- Then, we subtract the sum of numbers in the array from the total sum to get the missing number.

---

## 3. **[1822. Sign of the Product of an Array](https://leetcode.com/problems/sign-of-the-product-of-an-array/)**

### Problem Description

Given an integer array `nums`, return the sign of the product of all the numbers in the array. The sign is `1` if the product is positive, `-1` if the product is negative, and `0` if the product is zero.

### Solution

```cpp
int arraySign(int* nums, int numsSize) {
    int negativeCount = 0; 
    int zeroCount = 0;     
    for (int i = 0; i < numsSize; i++) {
        if (nums[i] == 0) {
            return 0;  // Product is zero if any number is zero
        } else if (nums[i] < 0) {
            negativeCount++;  // Count negative numbers
        }
    }
    return (negativeCount % 2 == 0) ? 1 : -1;  // Positive if even negatives, negative if odd negatives
}
```

### Explanation

- If any element in the array is zero, the product is zero.
- We count how many negative numbers are in the array. If the count is even, the product will be positive; if it's odd, the product will be negative.

---

## 4. **[2469. Convert the Temperature](https://leetcode.com/problems/convert-the-temperature/)**

### Problem Description

You are given a temperature in Celsius, and you need to convert it into both Kelvin and Fahrenheit. Return an array containing both converted values.

### Solution

```cpp
double* convertTemperature(double celsius, int* returnSize) {
    static double result[2];  // static array to hold the two conversion values
    result[1] = celsius * 9.0 / 5.0 + 32.0;  // Convert Celsius to Fahrenheit
    result[0] = celsius + 273.15;  // Convert Celsius to Kelvin
    *returnSize = 2;  // Set the return size to 2 since we are returning two values
    return result;  // Return the array with the two converted values
}
```

### Explanation

- We convert the given Celsius temperature to both Fahrenheit (`(C * 9/5) + 32`) and Kelvin (`C + 273.15`).
- The result is returned as an array of size 2, with the first element being the temperature in Kelvin and the second in Fahrenheit.

---
