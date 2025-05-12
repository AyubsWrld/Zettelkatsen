Let's say you have a library and an app:

```css
project/
├── include/
│   └── math.h
├── src/
│   └── math.cpp
├── main.cpp
├── CMakeLists.txt

```

```c
# CMakeLists.txt
add_library(MyLib src/math.cpp)
target_include_directories(MyLib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

add_executable(MyApp main.cpp)
target_link_libraries(MyApp PRIVATE MyLib)
```
___
Tags : #programming #cmake