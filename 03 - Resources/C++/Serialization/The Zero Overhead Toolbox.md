bitcast vs memcopy 
### **Top Left Code Block - `serialize`**

```cpp
std::size_t serialize(const address_book & book,
                      std::span<std::byte> data)
{
    zpp::bits::out out{data};
    if (auto result = out(book); failure(result)) {
        return 0;
    }
    return out.position();
}
```

---

### **Bottom Left Code Block - `deserialize`**

```cpp
std::size_t deserialize(address_book & book,
                        std::span<const std::byte> data)
{
    zpp::bits::in in{data};
    if (auto result = in(book); failure(result)) {
        return 0;
    }
    return in.position();
}
```

---

### **Right Side Bullet Points**

**The Zero Overhead Toolbox that zpp::bits uses**

1. **Make everything available for inline** – header only.  
    _Tip: Almost free to make everything `constexpr` as well._
    
2. **No virtual functions** – to maximize inlining
    
3. **Use concepts and templates to be fully generic** –  
    For example, “data” does not have to be `std::span`, can be a simple array, or `std::array`, or similar.
    
4. **Customize & optimize by `if constexpr`** –
    
    - Use `memcpy` where it would iterate byte by byte.
        
    - Serialization format determined in compile time
        
    - If a growing output buffer is needed, use `std::vector` or `std::string` which has `resize(..)`.  
        An `if constexpr` will detect it and use as needed.
        
5. **Zero overhead error handling, with alternatives** –  
    _Return values and then offer error checking alternatives for external usage:_
    

---

### **Bottom Right Snippets (Alternative usage examples)**

```cpp
zpp::bits::out out{data};
out(data).or_throw();
return out.position();
```

```cpp
zpp::bits::out out{data};
co_await out(data);
co_return out.position();
```

---

Let me know if you'd like a markdown version, explanation, or conversion to another serialization framework.