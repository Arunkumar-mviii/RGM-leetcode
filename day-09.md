
# LeetCode Solutions - Day 9

---

## 1. **[171. Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/)**

### Problem Description

Given a column title as appears in an Excel sheet, return its corresponding column number.

### Solution

```cpp
int titleToNumber(char* columnTitle) {
    int res = 0;
    for(int i = 0; columnTitle[i]; i++) {
        res = res * 26 + (columnTitle[i] - 65 + 1); 
    }
    return res;
}
```

### Explanation

- The column title can be treated as a base-26 number where 'A' = 1, 'B' = 2, ..., 'Z' = 26.
- We iterate through the columnTitle string, calculating the corresponding number by multiplying the current result by 26 and adding the value of the current character.

---

## 2. **[168. Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)**

### Problem Description

Given a positive integer `columnNumber`, return its corresponding column title as it appears in an Excel sheet.

### Solution

```cpp
char* convertToTitle(int columnNumber) {
    static char ans[8]; 
    int i = 6;          
    ans[7] = '\0';      
    while (columnNumber > 0) {
        columnNumber--;                       
        ans[i--] = (columnNumber % 26) + 'A'; 
        columnNumber /= 26;                  
    }
    return &ans[i + 1];
}
```

### Explanation

- To convert the number into an Excel column title, we repeatedly divide by 26, adjusting the remainder (to account for 'A' = 1, not 0).
- The result is constructed from right to left, so we need to reverse it at the end.

---

## 3. **[405. Convert a Number to Hexadecimal](https://leetcode.com/problems/convert-a-number-to-hexadecimal/)**

### Problem Description

Given an integer `num`, return its hexadecimal representation as a string.

### Solution

```cpp
char* toHex(int num) {
    static char hex[9]; 
    unsigned int n = num; 
    int i = 0;
    if (num == 0) return "0"; 
    while (n > 0) {
        int remainder = n % 16;
        hex[i++] = (remainder < 10) ? (remainder + '0') : (remainder - 10 + 'a'); 
        n /= 16; 
    }

    hex[i] = '\0';
    for (int j = 0; j < i / 2; j++) {
        char temp = hex[j];
        hex[j] = hex[i - j - 1];
        hex[i - j - 1] = temp;
    }
    return hex; 
}
```

### Explanation

- To convert an integer to hexadecimal, we repeatedly divide by 16, appending the corresponding hex digit to the result.
- The hexadecimal digits are mapped from `0-9` and `a-f`. If `n % 16` is less than 10, it's a digit, otherwise, it's a letter.
- After constructing the hexadecimal number, we reverse it to get the correct order.

---

## 4. **[415. Add Strings](https://leetcode.com/problems/add-strings/)**

### Problem Description

Given two non-negative integers `num1` and `num2` represented as string, return the sum of the two integers as a string.

### Solution

```cpp
char* addStrings(char* num1, char* num2) {
    static char result[10000]; 
    int i = strlen(num1) - 1; 
    int j = strlen(num2) - 1; 
    int carry = 0; 
    int k = 0; 

    while (i >= 0 || j >= 0 || carry > 0) {
        int sum = carry; 

        if (i >= 0) {
            sum += num1[i] - '0'; 
            i--; 
        }

        if (j >= 0) {
            sum += num2[j] - '0'; 
            j--; 
        }

        result[k++] = (sum % 10) + '0'; 
        carry = sum / 10; 
    }

    result[k] = '\0'; 

    for (int left = 0, right = k - 1; left < right; left++, right--) {
        char temp = result[left];
        result[left] = result[right];
        result[right] = temp;
    }

    return result; 
}
```

### Explanation

- We simulate the process of adding two numbers digit by digit, starting from the least significant digit.
- We maintain a carry value and iterate over both strings until all digits and the carry are processed.
- After constructing the result in reverse order, we reverse the string to get the correct result.

---

## 5. **[2544. Alternating Digit Sum](https://leetcode.com/problems/alternating-digit-sum/)**

### Problem Description

Given a positive integer `n`, return the alternating sum of its digits.

### Solution

```cpp
int alternateDigitSum(int n) {
    int reversed, sum = 0, a = 1;
    while (n != 0) {
        int digit = n % 10;  
        reversed = reversed * 10 + digit;  
        n = n / 10; 
    }
    while (reversed != 0) {
        int digit1 = reversed % 10;
        sum += a * digit1;
        a = a * -1;
        reversed = reversed / 10;
    }
    return sum;
}
```

### Explanation

- The function first reverses the digits of the number `n` and stores it in `reversed`.
- Then, it alternates adding and subtracting the digits from the reversed number, keeping track of the alternating sign with the variable `a`.

---

## 6. **[3304. Find the K-th Character in String Game I](https://leetcode.com/problems/find-the-k-th-character-in-string-game-i/)**

### Problem Description

In the string game, we begin with the string `"a"` and repeatedly apply the operation: replace the string with itself followed by the string's characters. For example:

- Step 1: `"a"`
- Step 2: `"aa"`
- Step 3: `"aaa"`

Given a value `k`, find the `k`-th character in the resulting string.

### Solution

```cpp
char kthCharacter(int k) {
    char initialChar = 'a';
    long long length = 1;

    while (length < k) {
        length *= 2;
    }

    while (k > 1) {
        long long halfLength = length / 2;

        if (k > halfLength) {
            k -= halfLength;
        } else {
            length = halfLength;
        }
    }

    return (initialChar + (k - 1)) % 26 + 'a';
}
```

### Explanation

- The string doubles in length each time, and we need to find which half the `k`-th character is in.
- We iteratively reduce the problem size until we find the position of `k` in the first string.
- The `k`-th character corresponds to a character from the sequence, which can be mapped to the alphabet.

---
