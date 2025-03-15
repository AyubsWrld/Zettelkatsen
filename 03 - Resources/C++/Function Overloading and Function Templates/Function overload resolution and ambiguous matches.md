In function overloading, the compiler must determine which overloaded function is the best match for a given function call, a process called **overload resolution**. If an overloaded function is not properly differentiated, a compile error occurs.

For non-overloaded functions, there is only one possible match, but for overloaded functions, the compiler follows a series of steps to find the best match:

1. **Exact Match**: The compiler first checks if any function has parameters that exactly match the function call's arguments. Trivial conversions (e.g., `int` to `const int`) also count as exact matches.
2. **Numeric Promotion**: If no exact match is found, the compiler applies numeric promotions (e.g., `char` and `bool` promoted to `int`, `float` promoted to `double`).
3. **Numeric Conversion**: If no match is found through promotion, numeric conversions (e.g., `char` to `double`) are applied.
4. **User-Defined Conversions**: If applicable, user-defined conversions (such as class type conversion operators) are considered.
5. **Ellipsis Matching**: If all else fails, the compiler looks for a function with an ellipsis (`...`).
6. **Compile Error**: If no match is found, a compile error occurs.

### Ambiguous Matches

If multiple overloaded functions are equally valid matches, the compiler issues an **ambiguous match error**, as it cannot determine the best option.

This process ensures that function calls resolve correctly while minimizing ambiguity in overloaded functions.

___
Tags :  #cppfunctions 

