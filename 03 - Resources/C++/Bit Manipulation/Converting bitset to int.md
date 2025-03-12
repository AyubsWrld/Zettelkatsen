> [!note] Purpose 
> #### Convert `std::bitset` to `int` using .to_ulong() method 

> [!example] 

```cpp
#inlcude <iostream>
#inlcude <bitset>

int main()
{
	std::bitset<8> bin = 0b0000'0001 ;
	int x = ( int ) bin.to_ulong(); 
	std::cout << x << std::endl ; 
	return 0;
}
```