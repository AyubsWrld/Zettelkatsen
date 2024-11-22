> [!tldr] 
> Utilizes a shift table which , when a mismatch is observed relative to a search key , the *n* remaining letters of the search key which matched prior to the mismatch can be skipped . 

Sure! Let's break it down in simple terms.

### What is Horspool’s Algorithm?

Horspool’s algorithm is a pattern-matching algorithm used to find a given word (pattern) in a larger body of text. It works by comparing characters in the pattern and text from right to left and uses a **precomputed table** to decide how far to shift the pattern when a mismatch occurs.

The goal is to shift the pattern as far as possible to save time without missing a potential match.

---

### Key Idea

When a mismatch happens, the **character in the text** that is aligned with the **last character of the pattern** determines the size of the shift. Horspool uses a **"bad character rule"** to compute the shift size for every character in the text.

---

### Shift Table

A **shift table** is precomputed before searching begins. It determines how far to move the pattern when a mismatch happens.

#### How to Compute the Shift Table:

1. Assume every character can cause the pattern to shift by its full length (the safest case).
2. Go through the pattern, left to right (except the last character), and for each character:
    - Set the shift value to the distance from that character to the **last character** in the pattern.

---

#### Example: Pattern `BARBER`

- The pattern's length is 6.
- We'll create a shift table for all possible characters.

**Steps to Compute the Table:**

1. Initially, set all characters' shift values to 6 (pattern length).
2. For each character in `BARBER` (except the last `R`):
    - For `B` (at index 0): Distance to the last `R` is 6−1−0=56 - 1 - 0 = 5.
    - For `A` (at index 1): Distance to the last `R` is 6−1−1=46 - 1 - 1 = 4.
    - For `R` (at index 2): Distance to the last `R` is 6−1−2=36 - 1 - 2 = 3.
    - For `B` (at index 3): Distance to the last `R` is 6−1−3=26 - 1 - 3 = 2.
    - For `E` (at index 4): Distance to the last `R` is 6−1−4=16 - 1 - 4 = 1.

#### Final Shift Table:

| Character  | Shift |
| ---------- | ----- |
| B          | 2     |
| A          | 4     |
| R          | 3     |
| E          | 1     |
| All others | 6     |

---

### Searching with the Shift Table

1. Align the pattern with the start of the text.
2. Compare characters in the pattern with characters in the text **from right to left**.
3. If there's a mismatch, check the text character causing the mismatch in the shift table:
    - Shift the pattern by the value in the table for that character.
4. Repeat until you reach the end of the text.

---

### Why is This Efficient?

Instead of always shifting by one position (as in brute force), Horspool skips unnecessary checks by shifting farther when it knows a character doesn't matter for the current match.

---

### Example Search with `BARBER`:

Text: `... CBARBERZ ...`

1. Start with the last `R` of `BARBER` aligned with the `B` in the text. Mismatch!
    
    - Use the shift table for `B`. Shift by 2.
2. Align the pattern again, compare from the last character. Match found!
    


___

Tags : #programming #algorithms 