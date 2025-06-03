A parameter pack holds and arbitrary number of parameters and values. 

```cpp
// Parameter Pack ( Holds and arbitrary number of items ) 
template<typename... T , typename... U>
auto function_results( T(&...f)) // T1( &f1 )( U1 u ) , T2( &f2 )(U2 u)  , T3( &f3 )()  
{
  return std::tuple( f()...); // f1() , f2() , f3() 
}
```

---
Tags: #cpp #parameter-pack