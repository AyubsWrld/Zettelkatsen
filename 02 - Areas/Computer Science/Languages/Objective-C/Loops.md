Here are brief notes on loop structures and control statements in Objective-C:

---

## Loop Structures

### 1. **`while` Loop**
- **Description**: Repeats code while a condition is true. Tests the condition before the loop body.
- **Syntax**:
  ```objective-c
  while (condition) {
      // code to execute
  }
  ```

### 2. **`for` Loop**
- **Description**: Executes a block of code a specified number of times, managing the loop variable.
- **Syntax**:
  ```objective-c
  for (initialization; condition; increment) {
      // code to execute
  }
  ```

### 3. **`do...while` Loop**
- **Description**: Similar to `while`, but tests the condition after the loop body executes.
- **Syntax**:
  ```objective-c
  do {
      // code to execute
  } while (condition);
  ```

### 4. **Nested Loops**
- **Description**: One or more loops inside another `while`, `for`, or `do...while` loop.
- **Example**:
  ```objective-c
  for (int i = 0; i < 3; i++) {
      for (int j = 0; j < 3; j++) {
          // code to execute
      }
  }
  ```

## Loop Control Statements

### 1. **`break` Statement**
- **Description**: Exits the loop or `switch` statement immediately, transferring control to the statement following the loop or `switch`.
- **Syntax**:
  ```objective-c
  break;
  ```

### 2. **`continue` Statement**
- **Description**: Skips the remaining code in the loop body and immediately retests the loop condition.
- **Syntax**:
  ```objective-c
  continue;
  ```

## Infinite Loop
- **Description**: A loop that runs indefinitely because the condition never becomes false.
- **Example**:
  ```objective-c
  #import <Foundation/Foundation.h>

  int main() {
      for (;;) {
          NSLog(@"This loop will run forever.\n");
      }
      return 0;
  }
  ```

---

These notes cover the basic types of loops and control statements in Objective-C, along with the concept of infinite loops.


___

Tags : #objective-c #language 