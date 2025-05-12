```c
cmake_minimum_required(VERSION 3.15...4.0)

project(Calculator LANGUAGES CXX)

add_library(calclib STATIC src/calclib.cpp include/calc/lib.hpp)
target_include_directories(calclib PUBLIC include)
target_compile_features(calclib PUBLIC cxx_std_11)

add_executable(calc apps/calc.cpp)
target_link_libraries(calc PUBLIC calclib)
```

**What does this do?**
- Ensures CMake version is at least 3.15 and gives a compatibility range up to 4.0 (the `...` syntax means the project will warn if run with a version newer than 4.0, unless compatibility features break).
- Declares a project named `Calculator` and specifies it uses the C++ language.
- Creates a static library target named `calclib`.It includes `src/calclib.cpp` and `include/calc/lib.hpp` in its compilation.
- `calclib` needs the `include/` directory to compile. Because it's `PUBLIC`, any target that links against `calclib` (like `calc`) will also have this include path automatically added. **Include is a directory path**. 
- Ensures `calclib` is compiled with **at least C++11** support.
- creates a target executable, `calc`, with source files `apps/calc.cpp`. Because it’s `PUBLIC`, anything that links against `calclib` (like `calc`) will also be required to support C++11.
- Links the target `calc` ( which is an executable to be compiled ) with the the library `calclib`. `PUBLIC` is utilized so that anything included within `calclib` is included by the members of `calclib` are included within calc. 
___
Tags : #programming #cmake