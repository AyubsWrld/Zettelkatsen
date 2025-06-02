____
##### [[Initializer-lists]] : 

```cpp
template <typename... T>
std::tuple foo( T... t )
{
	std::tuple<T...> retv = tuple( t... ) ; 
	return retv ; 
}
```

Conceptually, such a pack expansion is equivalent to a comma-separated list of instances of the pattern

___
##### [[Base Specifier Lists]] : 

```cpp

```

to specify one base class for each member of a type parameter pack, e.g.:

___

#### [[Member-initializer List]] : 

When initializing base classes in a mem-initializer list in a class constructor, the pack expansion initializes a list of base classes based on a type parameter pack:

____

##### [[Template Argument Lists]] : 

as in std::tuple, the pack expands to the equivalent of a comma-separated list of template arguments.

___
##### [[Lambda]] Capture Lists : 

In lambda capture lists, the pattern expansion is equivalent to a comma-separated list of captures. E.g.,

```cpp
template<typename... T>
void foo( T... args ) 
{
	auto x = [args...]{ /*  do something here*/} ; 
	x() ; 
}
```


##### Inside Function parameters and Template Parameters : 

Inside function parameters and template parameters, a pack expansion behaves like a comma separated list of patterns.

---
Tags: #cpp #parameter-pack