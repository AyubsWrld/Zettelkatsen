## `memcpy( destination , source , sizeof(source))`

-  **Purpose** : Copies one data from one block of memory to another . 
-  **Example** 
 ```c
 #include                                                                                                                                                                                                                                                           
#include                                                                                                                                                                                                                                                          
int main(){                                                                                                                                                                                                                                                                 
  int arr[10] = {0 * 10}  ;                                                                                                                                                                                                                                                 
  int dest[10] ;                                                                                                                                                                                                                                                            
  memcpy( dest , arr , sizeof(int) * 10) ;                                                                                                                                                                                                                                  
  printf("%d\n" , dest[2]) ;                                                                                                                                                                                                                                                
  return 0 ;                                                                                                                                                                                                                                                                
}
``` 

___
Tags : #programming #c #language 