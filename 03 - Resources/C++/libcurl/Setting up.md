Setting up libcurl goes as follows...

```cpp
CURL* curl = curl_easy_init() // Initialize handle 
CURLcode res = curl_easy_setopt(curl , CURLOPT_URL , "URL/TO/SERVER")  ;

// Check if res returned non-zero exit 

if ( res ) {
	//handle error here 
}

```


___
Tags : #progarmming #Networking #cpp