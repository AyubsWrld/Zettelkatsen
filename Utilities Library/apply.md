Iterating over a tuple ; 

```cpp
  auto tuple = std::make_tuple( 1 , 2 , 3 , 'a' , 'b' ) ; 
  std::apply( [&]( auto&&... args ){ ( ( std::cout << args << " "  ), ...) ; } , tuple ) ;  

```

```cpp
  auto tuple = std::make_tuple( 2 , 2 , 3 , 3 , 3 ) ; 
  std::apply( [&]( auto&&... args ){ ( ( std::cout << args++ << " "  ), ...) ; } , tuple ) ;  
  std::cout << std::endl ; 
  std::apply( [&]( auto&&... args ){ ( ( std::cout << args << " "  ), ...) ; } , tuple ) ;  
```

---
Tags: #cpp #utilities