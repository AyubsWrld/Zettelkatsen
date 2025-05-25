A captured parameter pack must be used in a [[Pattern]] that is expanded with an ellipsis (...). The length of a pattern determines the number of times the pattern is conceptually replicated in the expansion, once for each position in the expanded pack(s). For example: 

```cpp
void dummy( auto&&... ) {} // conceptually the same

template<typename... T>
void dummy( T&&... ){} 


template<std::same_as<char> ...C>
void expand(C... c)
{
	std::tuple<C...> tpl(c...) ; 
	const char msg[] = { C(std::toupper(c))... , '\0' }; 
	dummy( msg , c... ) ; 
}

```

expand captures a template parameter pack `C` consisting of a sequence of zero or more types, all of which must be char because of our use of the std::same_as concept. 


---
Tags: #cpp #parameter-pack