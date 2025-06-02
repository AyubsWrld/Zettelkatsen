```cpp
template <typename... Args>
std::vector<uint8_t> serialize(const std::string& function_name, Args&&... arguments) {
    using ArgsTuple = std::tuple<typename std::decay_t<std::remove_reference_v<Args>>...>;
    ArgsTuple tuple = std::make_tuple(arguments...);
}
```
