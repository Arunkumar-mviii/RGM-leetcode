
# LeetCode Solutions - Day 2

---

## 1. **[2651. Calculate Delayed Arrival Time](https://leetcode.com/problems/calculate-delayed-arrival-time/)**

### Problem Description

Given the `arrivalTime` and `delayedTime`, calculate the arrival time after the delay. The time is given in 24-hour format, and the result should be returned in 24-hour format as well.

### Solution

```cpp
int findDelayedArrivalTime(int arrivalTime, int delayedTime) {
    return (arrivalTime + delayedTime) % 24;
}
```

### Explanation

- The delayed arrival time is calculated by adding the `arrivalTime` and `delayedTime`, then taking the result modulo 24 to ensure it falls within a 24-hour range.

---

## 2. **[2485. Find the Pivot Integer](https://leetcode.com/problems/find-the-pivot-integer/)**

### Problem Description

You are given an integer `n`. The task is to find the pivot integer such that the sum of all integers from 1 to `pivot` equals the sum of all integers from `pivot` to `n`. Return the pivot integer, or -1 if there is no such integer.

### Solution

```cpp
int pivotInteger(int n) {
    int sum = n * (n + 1) / 2;  
    int pivot = sqrt(sum);     
    return (pivot * pivot == sum) ? pivot : -1; 
}
```

### Explanation

- The sum of integers from `1` to `n` is `n * (n + 1) / 2`.
- To find the pivot integer, we check if the square root of the total sum is an integer. If so, this integer is the pivot.

---

## 3. **[2600. K Items With the Maximum Sum](https://leetcode.com/problems/k-items-with-the-maximum-sum/)**

### Problem Description

Given `k` items with possible values `1`, `0`, or `-1`, the task is to determine the maximum sum we can get by selecting `k` items.

### Solution

```cpp
int kItemsWithMaximumSum(int numOnes, int numZeros, int numNegOnes, int k) {
    return (k <= numOnes) ? k : 
           (k <= numOnes + numZeros) ? numOnes : 
           numOnes - (k - numOnes - numZeros);
}
```

### Explanation

- We first check if `k` items can be chosen from the `numOnes` category.
- If not, we check how many items can be taken from `numOnes` and `numZeros`.
- Any remaining items are taken from `numNegOnes`.

---

## 4. **[2549. Count Distinct Numbers on Board](https://leetcode.com/problems/count-distinct-numbers-on-board/)**

### Problem Description

Given an integer `n`, the task is to find the number of distinct integers on a board after a series of moves.

### Solution

```cpp
int distinctIntegers(int n) {
    return (n == 1) ? 1 : n - 1;
}
```

### Explanation

- For `n = 1`, there is only one distinct integer on the board.
- For any other value of `n`, there are `n - 1` distinct integers.

---

## 5. **[2769. Find the Maximum Achievable Number](https://leetcode.com/problems/find-the-maximum-achievable-number/)**

### Problem Description

Given an integer `num` and an integer `t`, find the maximum achievable number after `t` operations. Each operation can increase `num` by 2.

### Solution

```cpp
int theMaximumAchievableX(int num, int t) {
    return num + t * 2;
}
```

### Explanation

- Each operation increases `num` by 2. Therefore, the maximum achievable number is simply `num + t * 2`.

---

## 6. **[2806. Account Balance After Rounded Purchase](https://leetcode.com/problems/account-balance-after-rounded-purchase/)**

### Problem Description

Given the `purchaseAmount`, return the account balance after rounding the purchase amount to the nearest multiple of 10, starting with an initial balance of 100.

### Solution

```cpp
int accountBalanceAfterPurchase(int purchaseAmount) {
    int initialBalance = 100;
    int roundedAmount = ((purchaseAmount + 5) / 10) * 10;
    int finalBalance = initialBalance - roundedAmount;
    return finalBalance;
}
```

### Explanation

- The purchase amount is rounded to the nearest multiple of 10.
- The final balance is calculated by subtracting the rounded purchase amount from the initial balance of 100.

---

## 7. **[2582. Pass the Pillow](https://leetcode.com/problems/pass-the-pillow/)**

### Problem Description

There are `n` children standing in a circle. A pillow is passed in a circular manner, and the task is to determine which child will have the pillow after a given time.

### Solution

```cpp
int passThePillow(int n, int time) {
    int pos = time % (2 * (n - 1)); 
    return (pos < n) ? (pos + 1) : (2 * n - pos - 1); 
}
```

### Explanation

- The pillow passing follows a circular pattern with a period of `2 * (n - 1)`.
- We use modulo to find the position of the child holding the pillow after `time` seconds.

---

## Extra Problem for Day - 2

### **[3178. Find the Child Who Has the Ball After K Seconds](https://leetcode.com/problems/find-the-child-who-has-the-ball-after-k-seconds/)**

### Problem Description

Given `n` children and a time `k`, find out which child will have the ball after `k` seconds.

### Solution

```cpp
int numberOfChild(int n, int k) {
   int pos = k % (2 * (n - 1));    
    return pos < n ? pos : 2 * (n - 1) - pos;
}                   
```

### Explanation

- Similar to the previous problem, the ball passes in a circular pattern with a period of `2 * (n - 1)`. We use modulo to determine the child who will have the ball after `k` seconds.
