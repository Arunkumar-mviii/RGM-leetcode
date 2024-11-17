
# LeetCode Solutions - Day 7

---

## 1. **[1217. Minimum Cost to Move Chips to the Same Position](https://leetcode.com/problems/minimum-cost-to-move-chips-to-the-same-position/)**

### Problem Description

There are `positionSize` chips, and their positions are stored in an array `position`. You need to return the minimum cost to move all chips to the same position. The cost for moving a chip depends on whether it is moved to an even or odd position.

### Solution

```cpp
int minCostToMoveChips(int* position, int positionSize) {
    int oc = 0;  // Odd count
    int ec = 0;  // Even count
    for(int i = 0; i < positionSize; i++) {
        if(position[i] % 2 == 0)
            ec++;
        else
            oc++;
    }
    return oc < ec ? oc : ec;
}
```

### Explanation

- We count how many chips are at odd positions (`oc`) and even positions (`ec`).
- The minimum cost to move all chips to one position will be the smaller count of chips in either odd or even positions, since it costs 1 to move from even to odd and vice versa.

---

## 2. **[1232. Check If It Is a Straight Line](https://leetcode.com/problems/check-if-it-is-a-straight-line/)**

### Problem Description

Given `coordinates` of points in a 2D plane, return `true` if they make a straight line, and `false` otherwise.

### Solution

```cpp
bool checkStraightLine(int** coordinates, int coordinatesSize, int* coordinatesColSize) {
    int x1 = coordinates[0][0], y1 = coordinates[0][1];
    int x2 = coordinates[1][0], y2 = coordinates[1][1];

    for (int i = 2; i < coordinatesSize; i++) {
        int x3 = coordinates[i][0], y3 = coordinates[i][1];
        if ((x2 - x1) * (y3 - y2) != (y2 - y1) * (x3 - x2)) {
            return false;  // Not in a straight line
        }
    }
    return true;  // All points are on the same line
}
```

### Explanation

- The equation for checking if three points are on the same straight line is derived from the determinant of the matrix formed by the points. If the area of the triangle formed by three points is zero, they are collinear.
- We check this condition for all points.

---

## 3. **[2455. Average Value of Even Numbers That Are Divisible by Three](https://leetcode.com/problems/average-value-of-even-numbers-that-are-divisible-by-three/)**

### Problem Description

Given an array `nums`, find the average of all even numbers that are divisible by 3.

### Solution

```cpp
int averageValue(int* nums, int numsSize) {
    int sum = 0;
    int count = 0;
    for (int i = 0; i < numsSize; i++) {
        if (nums[i] % 2 == 0 && nums[i] % 3 == 0) {
            sum += nums[i];
            count++;
        }
    }
    return count > 0 ? sum / count : 0;
}
```

### Explanation

- We iterate through the array and check if a number is even and divisible by 3.
- If such a number is found, we add it to `sum` and increment the `count`.
- If there are numbers that satisfy the condition, we return the average. If not, we return `0`.

---

## 4. **[2535. Difference Between Element Sum and Digit Sum of an Array](https://leetcode.com/problems/difference-between-element-sum-and-digit-sum-of-an-array/)**

### Problem Description

Given an array `nums`, find the absolute difference between the sum of the elements and the sum of the digits of each element.

### Solution

```cpp
int differenceOfSum(int* nums, int numsSize) {
    int elementSum = 0;
    int totalDigitSum = 0;
    for (int i = 0; i < numsSize; i++) {
        elementSum += nums[i];
        int num = nums[i];
        while (num > 0) {
            totalDigitSum += num % 10;
            num /= 10;
        }
    }
    return abs(elementSum - totalDigitSum);
}
```

### Explanation

- We compute the sum of all elements in the array (`elementSum`).
- We compute the sum of the digits of each element and add it to `totalDigitSum`.
- Finally, we return the absolute difference between these two sums.

---

## 5. **[1512. Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/)**

### Problem Description

Given an array `a`, return the number of good pairs. A good pair `(i, j)` is such that `a[i] == a[j]` and `i < j`.

### Solution

```cpp
int numIdenticalPairs(int* a, int n) {
    int pc = 0;  // Good pair count
    for(int i = 0; i < n; i++) {
        for(int j = i + 1; j < n; j++) {
            if(a[i] == a[j]) ++pc;  // Count good pairs
        }
    }
    return pc;
}
```

### Explanation

- We iterate through all pairs `(i, j)` in the array and check if `a[i] == a[j]`.
- We count such pairs and return the count.

---
