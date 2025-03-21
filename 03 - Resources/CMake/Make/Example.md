Your `Makefile` has a few issues:

1. **Mismatch between source and object files**:
    
    - `PREREQUISITE=main.c` should likely be `main.cpp` if you're using `g++`.
    - `OBJ=loglevels.cpp` should be `OBJ=loglevels.o`, as object files are typically compiled separately before linking.
2. **Missing compilation rule for `loglevels.o`**:
    
    - You need to compile `loglevels.cpp` into `loglevels.o` before linking.
3. **More explicit dependencies**:
    
    - Make sure `TARGET` depends on the object files.

### Fixed `Makefile`:

```makefile
CC=g++
CFLAGS=-I../include/ -Wall -Wextra -std=c++17
TARGET=exec
SRCS=main.cpp loglevels.cpp
OBJS=$(SRCS:.cpp=.o)

$(TARGET): $(OBJS)
	$(CC) $(OBJS) -o $(TARGET)

%.o: %.cpp
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(OBJS) $(TARGET)
```

### Changes:

- **Added `CFLAGS`**: Includes warning flags and `std=c++17` for better safety.
- **Changed `SRCS` to automatically include all relevant source files**.
- **Added an explicit rule to compile `.cpp` files into `.o`**.
- **Added a `clean` rule** to remove object files and the binary.

Now you can run:

```sh
make    # To build
make clean   # To remove compiled files
```

If the `exec` file is not being generated, let's troubleshoot:

### Check the Makefile Again

Here’s a refined version of your `Makefile` with debugging output:

```makefile
CC=g++
CFLAGS=-I../include/ -Wall -Wextra -std=c++17
TARGET=exec
SRCS=main.cpp loglevels.cpp
OBJS=$(SRCS:.cpp=.o)

all: $(TARGET)

$(TARGET): $(OBJS)
	@echo "Linking: $(TARGET)"
	$(CC) $(OBJS) -o $(TARGET)

%.o: %.cpp
	@echo "Compiling: $<"
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(OBJS) $(TARGET)
```

### Steps to Check:

1. **Run `make` and observe the output:**
    
    ```sh
    make
    ```
    
    You should see messages like:
    
    ```
    Compiling: main.cpp
    Compiling: loglevels.cpp
    Linking: exec
    ```
    
2. **Check if `exec` exists after compilation:**
    
    ```sh
    ls -l exec
    ```
    
    If it doesn’t exist, check the object files:
    
    ```sh
    ls -l *.o
    ```
    
3. **Manually compile to check for errors:**
    
    ```sh
    g++ -I ../include/ -Wall -Wextra -std=c++17 -c main.cpp loglevels.cpp
    g++ main.o loglevels.o -o exec
    ```
    
    If this works but `make` does not, then something is wrong with the Makefile.
    

### If `exec` is Still Missing:

- **Check for compilation errors** in `main.cpp` and `loglevels.cpp`.
- **Run `make clean && make`** to ensure old object files aren’t interfering.
- **Make sure you are in the correct directory** when looking for `exec`.

Let me know what the output says! 🚀
___
Tags : #programming #cmake