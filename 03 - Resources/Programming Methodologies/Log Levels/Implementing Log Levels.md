```cpp
#include <iostream>
#include <vector>
#include <cassert>
#include <chrono>


enum LogLevel{
  TRACE,
  DEBUG,
  INFO,
  WARN,
  ERROR
};

void log( LogLevel level , const std::string& message )
{
  switch (level) {
    case TRACE :
      std::cout << "\033[34m[TRACE]\033[0m " << message << std::endl ;
      break;

    case DEBUG :
      std::cout << "\033[36m[DEBUG]\033[0m " << message << std::endl ;
      break;
      
    case INFO  :
      std::cout << "\033[32m[INFO]\033[0m " << message << std::endl ;
      break;

    case WARN  :
      std::cout << "\033[33m[WARN]\033[0m " << message << std::endl ;
      break;

    case ERROR :
      std::cout << "\033[31m[ERROR]\033[0m " << message << std::endl ;
      break ;
  }
}


int main (int argc, char *argv[]) 
{
  assert( fptr && "Could not open the file");
  log( TRACE , "Application Started") ;
  log( DEBUG, "Application Started") ;
  log( WARN, "Application Started") ;
  log( ERROR, "Application Started") ;
  log( INFO, "Application Started") ;
  return 0;
}



```
____
Tags : #methodologies #programming 