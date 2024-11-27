```javascript
function horsepool(pattern, text) {
  const shiftTable = createShiftTable(pattern); // Step 1: Create shift table
  const m = pattern.length;
  const n = text.length;
  
  let i = m - 1; // Start comparison from the end of the pattern

  while (i < n) {
    let k = 0; // Number of matched characters
    // Compare the pattern with text from right to left
    while (k < m && pattern[m - 1 - k] === text[i - k]) {
      k++;
    }
    
    if (k === m) {
      return i - m + 1; // Match found, return starting index
    }
    
    // Mismatch: Use the shift table
    const shift = shiftTable[text[i]] || m; // Default shift if character not in pattern
    i += shift; // Update index
  }

  return -1; // No match found
}

function createShiftTable(pattern) {
  const table = {};
  const m = pattern.length;

  for (let i = 0; i < m - 1; i++) {
    table[pattern[i]] = m - 1 - i;
  }

  return table;
}

```


---

Tags : #programming #algorithms 