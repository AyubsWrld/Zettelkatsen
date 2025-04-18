```cpp
typedef std::array<float, 4> FPlane ; 

void simple_print_plane( size_t count , ... )
{
  va_list args ; 
  va_start( args , count );
  for( size_t i = 0 ; i < count ; ++ i )
  {
    FPlane f = va_arg(args , FPlane) ; 
    printf( "X : %f , Y : %f , Z : %f , W : %f\n" , f[0] , f[1] , f[2] , f[3]);
  }
  va_end(args) ; 
}


int main(void)
{
  FPlane test{ 1.0f , 0.2f , 3.0f , 4.0f};
  FPlane text{ 1.0f , 0.2f , 3.0f , 4.0f};
  simple_print_plane( 2 , test , text  ) ; 
}
```

___
Tags : #cpp #variadic_functions