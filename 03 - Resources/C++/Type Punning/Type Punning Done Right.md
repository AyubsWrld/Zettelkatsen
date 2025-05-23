```cpp
void add_ulp(float& f)
{
    static_assert(sizeof(float) == sizeof(uint32_t));
    uint32_t tmp;
    memcpy(&tmp, &f, sizeof(float));
    ++tmp;
    memcpy(&f, &tmp, sizeof(float));
}
```

##### But doesn't the memcopying take ages?

- No because the compiler knows what your doing. 

```asm
next_ulp(float&):
    add DWORD PTR [rdi], 1
    ret
```
___
Tags : #programming #cpp 