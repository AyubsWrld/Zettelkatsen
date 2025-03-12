```cpp
#include <stdlib.h> /* for realloc */
#include <string.h> /* for memcpy */
```

```cpp
struct memory {
  char *response;
  size_t size;
};
```


#### Callback Function Flow 
___

```cpp
static size_t cb(char *data, size_t size, size_t nmemb, void *clientp)
{

  // Size passed in from the request + 1 , This is returned for checksum 
  size_t realsize = size * nmemb;

  //create pointer to 
  struct memory *mem = (struct memory *)clientp;
 
  char *ptr = realloc(mem->response, mem->size + realsize + 1);
  if(!ptr)
    return 0;  /* out of memory */
 
  mem->response = ptr;
  memcpy(&(mem->response[mem->size]), data, realsize);
  mem->size += realsize;
  mem->response[mem->size] = 0;
 
  return realsize;
}
```

#### Main Function Flow 
___
- Zero Initialize memory chunk 
- Declare a CURLcode to receive the value of return value of other curl functions ( This is for error handling ) .
- Create curl handle and check if the handle was created . 
	- If the handle was created setopt

```cpp
 
int main(void)
{
  struct memory chunk = {0};
  CURLcode res;
  CURL *curl = curl_easy_init()
  if(curl) {
    curl_easy_setopt( curl , CURLOPT_WRITEFUNCTION , cb ) 
    curl_easy_setopt( curl , CURLOPT_WRITEDATA , (void*) &chunk)  
    /* send a request */
    res = curl_easy_perform() ; 
    free(chunk.response);
    curl_easy_cleanup(curl) ; 
  }
}
```

___
Tags : #progarmming #cpp