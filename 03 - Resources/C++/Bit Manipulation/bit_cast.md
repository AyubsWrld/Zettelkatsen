>*"Every bit in the [[Value Representation]] of the returned `To` object is equal to the corresponding bit in the [[Object Representation]] of from. The values of padding bits in the returned `To` object are unspecified."*

Essentially what this is saying is that the [[Value representation]] ( the bytes which actually encode the object and have meaning ) are equivalent to the [[Object Representation]] of the From object. 

```cpp
struct A // 8 bytes 3 padding bytes added for char. 
{
	int a ;
	char b ; 
};

struct B // 8 bytes, no padding. 
{
	int a ;
	int b ; 
};

std::bit_cast<B>(A) ; // -> B.b contains padding bits of A . 
```

This function template is constexpr if and only if each of `To`, `From` and the types of all subobjects of `To` and `From`:

- is not a union type;
- is not a pointer type;
- is not a pointer to member type;
- is not a volatile-qualified type; and
- has no non-static data member of reference type.


```cpp
struct A 
{
	int a ;
	union A_U {
		float b;
		int c;
	}; 
};

struct B // 8 bytes, no padding. 
{
	int a ; 
	int b ; 
};

std::bit_cast<B>(A) // No longer constexpr
```

![[Pasted image 20250528131607.png]]
[GitHub - Tsche/repr: Reconstructible string representations and more](https://github.com/Tsche/repr)

[meta/include/em/meta/lists.h at master · HolyBlackCat/meta · GitHub](https://github.com/HolyBlackCat/meta/blob/master/include/em/meta/lists.h)
___
Tags : #programming #cpp 