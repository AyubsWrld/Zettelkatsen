The entire Graphic Rendition subset of the ANSI escape sequences have the form

```bash
\033[XXm
```

Where `XXX` is a series of semicolon-separated parameters. 

For example 
```cpp
std::cout<<"\033[31;1;4mHello\033[0m";
```

where the first part makes the text red (`31`), bold (`1`), underlined (`4`) and the last part clears all this (`0`).


____
Tags : #methodologies #programming 