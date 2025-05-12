Other common uses for generator expressions:

- Limiting an item to a certain language only, such as CXX, to avoid it mixing with something like CUDA, or wrapping it so that it is different depending on target language.
    
- Accessing configuration dependent properties, like target file location.
    
- Giving a different location for build and install directories.

That last one is very common. You’ll see something like this in almost every package that supports installing:

```c
target_include_directories(
    MyTarget
  PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)
```
___
Tags : #programming #cmake