The process of taking our [[Parameter Pack]] and expanding it to the individual parts it comprises of. This is done through suffixing the pattern with an ellipsis. Pack expansion is conceptually equivalent to having one copy of the pattern for each element of the parameter pack.

For example: 

```cpp
void print_strings( std::convertible_to<std::string_view ) auto&& ...s)
{
	for (auto v : std::initializer_list<std::string_view>{s...})
	{
	std:cout << v << ; 
	}
}

int main()
{
	print_strings( "one" , std::string{"two"}) ; 
}
```

Use of auto in the arguments of print_strings makes print_strings an [[Abbreviated Function Template]]. 

also the use of `auto&&` is known as a [[Forwarding Reference]]. This accepts both [[l-values]] and [[r-values]] regardless of [[cv-qualification]].  "one" in this case is an [[l-value]] and point to a specific location within the binary ( Surprisingly enough [[C-style string literal]]s are l-values and are stored in memory ) whereas the `std::string{"two"}` is a [[prvalue]]. 


---
Tags: #cpp #parameter-pack
