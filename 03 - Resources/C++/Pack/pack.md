##### Parameter Pack
___
Appears in the declaration of the template. 

```cpp
template <typename... T>
```

It is also important to mention that the parameter pack must be the last declared type within the template list. For instance...

```cpp
template<typename U, typename... Ts>   // Valid
struct valid;

// Invalid, parameter pack not at the end.  
template<typename... U, typename Ts>   
struct valid;
 
template<typename... Ts, typename U, typename=void>
void valid(U, Ts...);  // Works, Template argument deduction 
 
valid(1.0, 1, 2, 3);     
```

##### Pack Expansion
___
Appears in the body of the template. It is marked by a pattern followed by an ellipsis. For example 

```cpp
// Us expands to U1 , U2 , U...n
template<class... Us>
void f(Us... pargs) {}
 
// Ts expands to T1 , T2 , T...n
template<class... Ts>
void g(Ts... args)
{
	// Calling in to f(... Ts), expands the same with type ref . 
    f(&args...); 
}
 
g(1, 0.2, "a"); 

```

==If two packs appear in the same patter, they are expanded simultaneously , and they must have the same length.==

```cpp
template<typename...>
struct Tuple {};
 
template<typename T1, typename T2>
struct Pair {};
 
template<class... Args1>
struct zip
{
    template<class... Args2>
    struct with
    {
        typedef Tuple<Pair<Args1, Args2>...> type;
    };
};
```

---
Tags: #cpp #parameter-pack