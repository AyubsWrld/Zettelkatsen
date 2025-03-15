> [!tldr] 
> **C++17** within `<string_view>` header
> `std::string_view` helps us evade the costly task of copy initializing strings through the use of read-only access to C-style string literals. 

Used to combat the problem present within initializing strings : its very slow.

```cpp 
int main(){
	std::string name { "Ayub" }  ;
	std::cout << name << std::endl ; 
	return 0; 
}
```

Here we essentially made a copy just to destroy it after a single use. 

`std::string_view` provides access to read-only C-style string literals which circumvent the need to copy anything. 


___
Tags : #programming #cpp #cpp17