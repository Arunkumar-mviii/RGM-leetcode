# LeetCode Solutions - Day 10

---

## 1. **[3024. Type of Triangle](https://leetcode.com/problems/type-of-triangle/)**

### Problem Description

Given three integers representing the sides of a triangle, return the type of triangle (equilateral, isosceles, scalene, or none).

### Solution

```cpp
char* triangleType(int* nums, int numsSize) {
    if (nums[0] + nums[1] > nums[2] && nums[0] + nums[2] > nums[1] && nums[1] + nums[2] > nums[0]) {
        if (nums[0] == nums[1] && nums[1] == nums[2])
            return "equilateral";
        if (nums[0] == nums[1] || nums[1] == nums[2] || nums[0] == nums[2])
            return "isosceles";
        if (nums[0] != nums[1] && nums[1] != nums[2] && nums[2] != nums[0])
            return "scalene";
    }
    return "none";
}
```

### Explanation

- The function checks if the three sides form a valid triangle (sum of any two sides greater than the third).
- If the sides are equal, it's equilateral; if two sides are equal, it's isosceles; otherwise, it's scalene.
- If no valid triangle is formed, return "none".

---

## 2. **[389. Find the Difference](https://leetcode.com/problems/find-the-difference/)**

### Problem Description

Given two strings `s` and `t`, where `t` is created by random shuffling characters from `s` and adding one more letter, return the letter that was added.

### Solution

```cpp
char findTheDifference(char* s, char* t) {
    int charCount[128] = {0};
    for (int i = 0; s[i] != '\0'; i++)
        charCount[(int)s[i]]++;
    for (int i = 0; t[i] != '\0'; i++)
        charCount[(int)t[i]]--;
    for (int i = 0; i < 128; i++)
        if (charCount[i] == -1)
            return (char)i;
    return '\0';
}
```

### Explanation

- The function counts the frequency of characters in both strings.
- The difference in character frequencies will point to the additional character in `t`.

---

## 3. **[2864. Maximum Odd Binary Number](https://leetcode.com/problems/maximum-odd-binary-number/)**

### Problem Description

Given a binary string `s`, rearrange the digits in a way that forms the largest odd binary number possible.

### Solution

```cpp
char* maximumOddBinaryNumber(char* s) {
    int onesCount = 0, zerosCount = 0;
    for (int i = 0; s[i] != '\0'; i++) {
        if (s[i] == '1') {
            onesCount++;
        } else {
            zerosCount++;
        }
    }
    for (int i = 0; i < onesCount - 1; i++) {
        s[i] = '1';
    }
    for (int i = onesCount - 1; i < onesCount + zerosCount - 1; i++) {
        s[i] = '0';
    }
    s[onesCount + zerosCount - 1] = '1';
    s[onesCount + zerosCount] = '\0';
    return s;
}
```

### Explanation

- Count the number of `1`s and `0`s in the string.
- Rearrange the `1`s to the left, followed by `0`s, and make the last bit `1` to ensure the number is odd.

---

## 4. **[1684. Count the Number of Consistent Strings](https://leetcode.com/problems/count-the-number-of-consistent-strings/)**

### Problem Description

Given a string `allowed` and an array `words`, return the number of words in `words` that are consistent with `allowed`.

### Solution

```cpp
int countConsistentStrings(char * allowed, char ** words, int wordsSize) {
    int allowedFreq[26] = {0};
    for (int i = 0; allowed[i]; i++)
        allowedFreq[allowed[i] - 'a'] = 1;
    
    int consistentWord = 0;
    for (int i = 0; i < wordsSize; i++) {
        int flag = 1;
        for (int j = 0; words[i][j]; j++) {
            if (allowedFreq[words[i][j] - 'a'] == 0) {
                flag = 0;
                break;
            }
        }
        if (flag == 1)
            consistentWord++;
    }
    return consistentWord;
}
```

### Explanation

- For each word, we check if all characters belong to the `allowed` set (using a frequency array).
- If a word is consistent, it’s counted towards the result.

---

## 5. **[2525. Categorize Box According to Criteria](https://leetcode.com/problems/categorize-box-according-to-criteria/)**

### Problem Description

Given the dimensions and mass of a box, categorize it as "Bulky", "Heavy", "Both", or "Neither" based on the following criteria:

- A box is **Bulky** if its dimensions exceed 10,000 or if its volume exceeds 1 billion.
- A box is **Heavy** if its mass is greater than or equal to 100.

### Solution

```cpp
char* categorizeBox(int length, int width, int height, int mass) {
    long long volume = (long long)length * width * height;
    int isBulky = (length >= 10000 || width >= 10000 || height >= 10000 || volume >= 1000000000);
    int isHeavy = (mass >= 100);
    if (isBulky && isHeavy) {
        return "Both";
    } else if (isBulky) {
        return "Bulky";
    } else if (isHeavy) {
        return "Heavy";
    } else {
        return "Neither";
    }
}
```

### Explanation

- The function checks if the box meets the criteria for being bulky, heavy, or both by checking the dimensions and mass.

---

## 6. **[2351. First Letter to Appear Twice](https://leetcode.com/problems/first-letter-to-appear-twice/)**

### Problem Description

Given a string `s`, find the first letter to appear twice in it.

### Solution

```cpp
char repeatedCharacter(char* s) {
    int seen[26] = {0};
    for (int i = 0; s[i] != '\0'; i++) {
        int index = s[i] - 'a';
        if (seen[index]) {
            return s[i];
        }
        seen[index] = 1;
    }
    return '\0';
}
```

### Explanation

- The function uses an array to keep track of seen characters and returns the first character that appears twice.

---

## 7. **[1812. Determine Color of a Chessboard Square](https://leetcode.com/problems/determine-color-of-a-chessboard-square/)**

### Problem Description

Given a chessboard square (e.g., "a1"), determine if it is white or black.

### Solution

```cpp
bool squareIsWhite(char* c) {
    int row = c[0] - 97 + 1;
    int col = c[1] - 48 + 1;
    return (row + col) % 2 == 0;
}
```

### Explanation

- The square is white if the sum of the row and column indices is even; otherwise, it’s black.

---

## 8. **[3274. Check if Two Chessboard Squares Have the Same Color](https://leetcode.com/problems/check-if-two-chessboard-squares-have-the-same-color/)**

### Problem Description

Given two chessboard squares, determine if they are the same color.

### Solution

```cpp
bool checkTwoChessboards(char* c1, char* c2) {
    int col1 = c1[0] - 97 + 1;
    int row1 = c1[1] - 48 + 1;
    int col2 = c2[0] - 97 + 1;
    int row2 = c2[1] - 48 + 1;
    return (row1 + col1) % 2 == (row2 + col2) % 2;
}
```

### Explanation

- The function checks if the sum of the row and column indices for both squares are either both even or both odd, meaning they have the same color.

---

## 9. **[1903. Largest Odd Number in String](https://leetcode.com/problems/largest-odd-number-in-string/)**

### Problem Description

Given a numeric string, return the largest odd number that can be formed from its digits.

### Solution

```cpp
char* largestOddNumber(char* num) {
    int len = strlen(num);
    for (int i = len - 1; i >= 0; i

--) {
        if (num[i] % 2 != 0) {
            num[i + 1] = '\0';
            return num;
        }
    }
    return "";
}
```

### Explanation

- Starting from the rightmost digit, we find the first odd digit and return the substring that ends at that digit.

---

## 10. **[3222. Find the Winning Player in Coin Game](https://leetcode.com/problems/find-the-winning-player-in-coin-game/)**

### Problem Description

In a coin game with two players, determine who will win given two piles of coins.

### Solution

```cpp
char* losingPlayer(int x, int y) {
    int turns = 0;
    while (x >= 1 && y >= 4) {
        turns += 1;
        x -= 1;
        y -= 4;
    }
    if (turns % 2 == 0)
        return "Bob";
    return "Alice";
}
```

### Explanation

- The function simulates the coin game and returns the player who will lose based on the number of turns.

---
