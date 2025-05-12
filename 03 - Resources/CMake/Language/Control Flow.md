```c
if(variable)
    # If variable is `ON`, `YES`, `TRUE`, `Y`, or non zero number
else()
    # If variable is `0`, `OFF`, `NO`, `FALSE`, `N`, `IGNORE`, `NOTFOUND`, `""`, or ends in `-NOTFOUND`
endif()
# If variable does not expand to one of the above, CMake will expand it then try again
```

There are a variety of keywords as well, such as:

- Unary: `NOT`, `TARGET`, `EXISTS` (file), `DEFINED`, etc.
 
- Binary: `STREQUAL`, `AND`, `OR`, `MATCHES` (regular expression), `VERSION_LESS`, `VERSION_LESS_EQUAL` (CMake 3.7+), etc.
    
- Parentheses can be used to group
___
Tags : #programming #cmake