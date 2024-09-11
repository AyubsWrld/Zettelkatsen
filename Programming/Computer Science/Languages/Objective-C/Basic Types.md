## Objective-C Data Types

### Basic Types
- **Integer Types**: For whole numbers.
  - `char`, `int`, `short`, `long`
- **Floating-Point Types**: For decimal numbers.
  - `float`, `double`, `long double`

### Enumerated Types
- Used for variables with specific integer values.

### Void Type
- **`void`**: Indicates no value.
  - **Function Returns**: `void functionName(void);`
  - **Function Arguments**: `int rand(void);`

### Storage Sizes and Ranges

#### Integer Types

| Type             | Storage Size | Value Range                                          |
| ---------------- | ------------ | ---------------------------------------------------- |
| `char`           | 1 byte       | -128 to 127 or 0 to 255                              |
| `unsigned char`  | 1 byte       | 0 to 255                                             |
| `signed char`    | 1 byte       | -128 to 127                                          |
| `int`            | 2 or 4 bytes | -32,768 to 32,767 or -2,147,483,648 to 2,147,483,647 |
| `unsigned int`   | 2 or 4 bytes | 0 to 65,535 or 0 to 4,294,967,295                    |
| `short`          | 2 bytes      | -32,768 to 32,767                                    |
| `unsigned short` | 2 bytes      | 0 to 65,535                                          |
| `long`           | 4 bytes      | -2,147,483,648 to 2,147,483,647                      |
| `unsigned long`  | 4 bytes      | 0 to 4,294,967,295                                   |

#### Floating-Point Types

| Type          | Storage Size | Value Range            | Precision         |
| ------------- | ------------ | ---------------------- | ----------------- |
| `float`       | 4 bytes      | 1.2E-38 to 3.4E+38     | 6 decimal places  |
| `double`      | 8 bytes      | 2.3E-308 to 1.7E+308   | 15 decimal places |
| `long double` | 10 bytes     | 3.4E-4932 to 1.1E+4932 | 19 decimal places |

```objective-c
#import <Foundation/Foundation.h>
int main(){
	NSLog(@"Storage size of a char : %d" , sizeof(char)) ;  // prints 1 
	return 0 ; 
}
```
___

Tags : #objective-c  #language 