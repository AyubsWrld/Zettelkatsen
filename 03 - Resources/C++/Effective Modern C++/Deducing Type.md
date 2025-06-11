 > [!tldr] 
> ### Layman's Explanation of the Chapter

#### Understand template type deduction. 
Depending on what we pass to the template the compiler can deduce it's type. This is called [[Class Template Argument Deduction]]. This can occur in three ways: 

##### Case 1 : You pass by reference or by pointer.
____

```cpp
template<typename T>
void f(T& param); // param is a reference
```

- In this case if you pass in an `int`, `T` is treated as an int and f is specialized using an integer. 
- This retains [[cv-qualification]]. 
##### Case 2 : You pass by [[Universal Reference]]
____

```cpp
template<typename T>
void f(T&& param); // Universal reference
```

- If you pass an [[l-value]] , `T`  becomes `T&`. If you pass in an [[r-value]], `T` becomes `T&&`. 

##### Case 3 : You pass by value
____
- The compiler strips off references and `const` because the variable is being copied. 
- If you pass in `const int`, the compiler will treat it just like a regular `int`. 
- If you pass in an array by value it decays to a pointer. If you pass in a function by value it decays into a function pointer. 
 
```cpp
template<typename T>
void f(T param); // T is deduced as a pointer

template<typename T>
void f(T& param); // T is deduced as actual array type
```

#### Key Takeaways:
___
- References are ignored except for universal references. 
- constness is casted away if passing by value. 
- Arrays and functions turn into pointers unless passed by reference.
#### Why is matters ? 

____
#### Understand auto type deduction.

- Auto rules vs. template rules.
- How Auto deduces type. 
- Auto can sometimes give us types we don't want or may be unable to resolve a type itself. 

___

#### Understanding decltype.

##### What is decltype ? 
___
- **What is decltype(x)**: It informs us of the declaration type of some variable. 
- **When is it useful**: One use case might be when we want to return a type as an expression, Like when returning `c[i]` from a container. 

##### Using decltype(auto) 
___
We can use `decltype(auto)` to deduce the type of a return value. For example...

```cpp
decltype(auto) foo()
{
	return x ;  // -> returns decltype(x) ; 
}
```

we should be careful however, as 

```cpp 
return x ; // returns by value. 
return (x) ; // returns by reference. 
```

**Why would returning by reference be detrimental in this case?**: 
Had x been a local variable, returning x by reference would be catastrophic.

**When might this be useful?**:  Use in functions ( trailing return type ) Sometimes, you want to **return whatever `c[i]` is**, even if it’s a reference:

```cpp
template<typename Container, typename Index>
decltype(auto) get(Container&& c, Index i) {
  return std::forward<Container>(c)[i];
}
```

**Why do it this way?** This is precise — it **preserves the exact type**, including reference-ness. ( How ? ).

____
#### Know how to view deduced types. 

Really only concern myself with this compiler trick 

```cpp

template <typename T>
class TD; 

TD<decltype(x)> xType; // Gives compiler regarding the type. 
```





#### Things you should be able to answer: 

- How does `decltype` work ? 
- Why should we use `decltype`?
- When should we use `decltype`?
- What happens when we wrap something in `()`? 
- What does `decltype(auto)` do and when should it be used ? 


